<template>
<div class="max-h-80 overflow-auto scroll">
<!--<main-box v-if="tasks.length === 0" class="border-b border-[#4D5066]">
    <task-box :task="NoTaskMessage"></task-box>
</main-box>-->
<div v-if="activeFilter === 'all' || activeFilter === 'completed'">
<main-box  v-for="task in setCompletedTasks"  :key="task.id" class="border-b border-[#4D5066]">
    <task-box @complete-task="setComplete" @remove-task="removeTast" :isCompletebox="true" :task="task"></task-box>
</main-box>
</div>
<div v-if="activeFilter === 'all' || activeFilter === 'active'">
<main-box v-for="task in setActiveTasks" :key="task.id" class="border-b border-[#4D5066]">
    <task-box @complete-task="setComplete" @remove-task="removeTast" :isCompletebox="false" :task="task"></task-box>
</main-box>
</div>

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
            },
        }
    },
    components: {
        MainBox,
        TaskBox,
    },
    computed: {
        setActiveTasks(){
            return this.tasks.filter(el => el.status === "active")
        },
        setCompletedTasks(){
            return this.tasks.filter(el => el.status === "complete")
        }
    },
    props:{
        tasks: {
            type: Array,
            required: true
        },
        activeFilter: {
            type: String,
            required: true
        }

    },
    emits: ['remove-task','complete-task'],

    methods: {
        removeTast(data){
            this.$emit('remove-task',data);
        },
        setComplete(data){
            this.$emit('complete-task',data)
        }
    }
}


</script>