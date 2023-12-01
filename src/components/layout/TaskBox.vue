<template>
    <div class="w-full flex justify-between items-center">
        <div class="flex items-center">
            <finish-button v-if="isCompletebox === false" @click="isComplete"></finish-button>
            <complete-icon v-else @click="isComplete"></complete-icon>
            <h2 class="ml-5" :class="setCompleteClass" >{{ task.content }}</h2>
        </div>
        <remove-button @click="isRemoved"></remove-button>
    </div>
</template>

<script>
import FinishButton from '../buttons/FinishButton.vue';
import RemoveButton from '../buttons/RemoveButton.vue';
import CompleteIcon from '../icons/CompleteIcon.vue';

export default{
    components: {
        FinishButton,
        RemoveButton,
        CompleteIcon,
    },

    props: {
        task: {
            type: Object,
            required: true
        },
        isCompletebox: {
            type: Boolean,
            required: false,
            default() {
                return false
            }
        }
    },

    emits: ['remove-task','complete-task'],
    computed: {
        setCompleteClass(){
          return this.isCompletebox === true ? "text-[#4D5066] line-through"  : "text-[#CACDE8]"
        }
    },
    methods: {
        isRemoved(){
            this.$emit('remove-task',this.task.id)
        },
        isComplete(){
            this.$emit('complete-task',this.task.id)
        },
    }
}

</script>