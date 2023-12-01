<template>
  <main-box :isDarkMode="isDarkMode" class="flex justify-between">
    <TasksAmount
      :tasksAmount="tasksAmount"
      :class="settextColor"
    ></TasksAmount>
    <div class="flex h-full gap-5">
      <filter-link @click="setType('all')" :class="setAll">All</filter-link>
      <filter-link @click="setType('active')" :class="setActive">Active</filter-link>
      <filter-link @click="setType('completed')" :class="setCompleted">Completed</filter-link>
    </div>
    <filter-link @click="clearComplete" :class="setButtonColor">Clear Completed</filter-link>
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
    },
    isDarkMode: {
      type: Boolean,
      required: true
    }
  },
  emits: ['set-link','clear-completed'],
  computed: {
    setAll(){
      if(this.isDarkMode === true) {
        return this.isActive === "all" ? "text-[#3A7BFD]" : "text-[#4D5066] hover:text-[#E4E5F1]"
      }else{
        return this.isActive === "all" ? "text-[#3A7BFD]" : "text-[#9394A5] hover:text-[#4D5066]" 
      }
    },
    setActive() {
      if(this.isDarkMode === true) {
        return this.isActive === "active" ? "text-[#3A7BFD]" : "text-[#4D5066] hover:text-[#E4E5F1]"
      }else{
        return this.isActive === "active" ? "text-[#3A7BFD]" : "text-[#9394A5] hover:text-[#4D5066]" 
      }
    },
    setCompleted(){
      if(this.isDarkMode === true) {
        return this.isActive === "completed" ? "text-[#3A7BFD]" : "text-[#4D5066] hover:text-[#E4E5F1]"
      }else{
        return this.isActive === "completed" ? "text-[#3A7BFD]" : "text-[#9394A5] hover:text-[#4D5066]" 
      }
    },
    settextColor(){
      return this.isDarkMode ? "text-[#4D5066]" : "text-[#9394A5]";
    },
    setButtonColor(){
      return this.isDarkMode ? "text-[#4D5066] hover:text-[#E4E5F1]" : "text-[#9394A5] hover:text-[#4D5066]"
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
