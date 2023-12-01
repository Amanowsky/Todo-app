<template>
    <div class="w-full flex justify-between items-center">
        <div class="flex items-center">
            <finish-button></finish-button>
            <h2 class="ml-5 text-[#CACDE8]" >{{ task.content }}</h2>
        </div>
        <remove-button @click="isCliced"></remove-button>
    </div>
</template>

<script>
import FinishButton from '../buttons/FinishButton.vue';
import RemoveButton from '../buttons/RemoveButton.vue';

export default{
    components: {
        FinishButton,
        RemoveButton,
    },

    props: {
        task: {
            type: Object,
            required: true
        }
    },

    emits: ['remove-task'],
    methods: {
        isCliced(){
            this.$emit('remove-task',this.task.id)
        }
    }
}

</script>