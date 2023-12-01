<template>
<div class="max-h-80 overflow-auto scroll">
<main-box v-if="tasks.length === 0" class="border-b border-[#4D5066]">
    <task-box :task="NoTaskMessage"></task-box>
</main-box>
<main-box v-for="task in tasks" :key="task.id" class="border-b border-[#4D5066]">
    <task-box @remove-task="removeTast" :task="task"></task-box>
</main-box>
</div>
</template>

<script>
import MainBox from './layout/MainBox.vue';
import TaskBox from './layout/TaskBox.vue';

export default{
    data(){
        return {
            NoTaskMessage: {
                id: null,
                content: "No task has been added",
                status: null,
            }            
        }
    },
    components: {
        MainBox,
        TaskBox,
    },
    props:{
        tasks: {
            type: Array,
            required: true
        },
    },
    emits: ['remove-task'],

    methods: {
        removeTast(data){
            this.$emit('remove-task',data);
        }
    }
}


</script>