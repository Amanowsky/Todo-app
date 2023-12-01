<template>
    <div class="w-full flex justify-between items-center">
        <div class="flex items-center">
            <finish-button @click="isComplete"></finish-button>
            <h2 class="ml-5 text-[#CACDE8]" >{{ task.content }}</h2>
        </div>
        <remove-button @click="isRemoved"></remove-button>
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

    emits: ['remove-task','complete-task'],
    methods: {
        isRemoved(){
            this.$emit('remove-task',this.task.id)
        },
        isComplete(){
            this.$emit('complete-task',this.task.id)
        }
    }
}

</script>