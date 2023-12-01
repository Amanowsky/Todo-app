<template>
  <main-box class="flex justify-between">
    <TasksAmount
      :tasksAmount="tasksAmount"
      class="text-[#4D5066]"
    ></TasksAmount>
    <div class="flex h-full gap-5">
      <filter-link @click="setType('all')" :class="setAll">All</filter-link>
      <filter-link @click="setType('active')" :class="setActive">Active</filter-link>
      <filter-link @click="setType('completed')" :class="setCompleted">Completed</filter-link>
    </div>
    <filter-link @click="clearComplete" class="text-[#4D5066] hover:text-[#E4E5F1]">Clear Completed</filter-link>
  </main-box>
</template>

<script>
import FilterLink from "./buttons/FilterLink.vue";
import MainBox from "./layout/MainBox.vue";
import TasksAmount from "./layout/TasksAmount.vue";

export default {
  components: {
    FilterLink,
    MainBox,
    TasksAmount,
  },
  props: {
    tasksAmount: {
      type: Number,
      required: true,
    },
    isActive: {
        type: String,
        required: true
    }
  },
  emits: ['set-link','clear-completed'],
  computed: {
    setAll(){
        return this.isActive === "all" ? "text-[#3A7BFD]" : "text-[#4D5066] hover:text-[#E4E5F1]"
    },
    setActive() {
        return this.isActive === "active" ? "text-[#3A7BFD]" : "text-[#4D5066] hover:text-[#E4E5F1]"
    },
    setCompleted(){
        return this.isActive === "completed" ? "text-[#3A7BFD]" : "text-[#4D5066] hover:text-[#E4E5F1]"
    }
  },
  methods: {
    setType(data){
        this.$emit('set-link',data)
    },
    clearComplete(){
      this.$emit('clear-completed');
    }
  }
};
</script>
