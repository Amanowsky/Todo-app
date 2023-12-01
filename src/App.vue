<template>
  <the-background :bgSrc="setBgImg" :color="setBgColor"></the-background>
  <main class="flex flex-col w-1/3 mt-24">
    <div class="flex justify-between items-center mb-10">
      <the-title
        title="T O D O"
        options="text-4xl font-bold tracking-wide"
      ></the-title>
      <darkmode-button
        @toggle-darkmode="setDarkMode"
        :darkMode="darkMode"
      ></darkmode-button>
    </div>
    <task-input @task-added="addTasks"></task-input>
    <div class="mt-5">
      <task-area @remove-task="removeTast" :tasks="tasks"></task-area>
    </div>
    <div class="flex">
      <navi-bar @set-link="setActive" class="text-sm" :isActive="activeLink" :tasksAmount="active_tasks.length"></navi-bar>
    </div>
  </main>
</template>

<script>
import TheBackground from "./components/layout/TheBackground.vue";
import TheTitle from "./components/TheTitle.vue";
import DarkmodeButton from "./components/buttons/DarkmodeButton.vue";
import TaskInput from "./components/TaskInput.vue";
import TaskArea from "./components/TaskArea.vue";
import NaviBar from "./components/NaviBar.vue";

import bg_desktop_dark from "./assets/images/bg-desktop-dark.jpg";
import bg_desktop_light from "./assets/images/bg-desktop-light.jpg";

export default {
  components: {
    TheBackground,
    TheTitle,
    DarkmodeButton,
    TaskInput,
    TaskArea,
    NaviBar,
  },
  data() {
    return {
      bg_desktop_dark,
      bg_desktop_light,
      darkMode: true,
      activeLink: 'all',

      tasks: [],
      active_tasks: [],
      completed_tasks: [],
    };
  },
  computed: {
    setBgColor() {
      return this.darkMode ? "bg-[#161722]" : "bg-[#ffffff]";
    },
    setBgImg() {
      return this.darkMode ? bg_desktop_dark : bg_desktop_light;
    },
  },
  watch: {
    tasks() {
      console.log("test");
      this.active_tasks = this.tasks.filter((el) => el.status === "active");
    },
  },
  methods: {
    setDarkMode() {
      this.darkMode = !this.darkMode;
    },
    addTasks(item) {
      const task = {
                id: new Date().toISOString(),
                content: item,
                status: 'active'
            };
            this.tasks.push(task);
            this.tasks = this.tasks.slice(); 

    },
    removeTast(task) {
      const index = this.tasks.findIndex((el) => el.id === task);
      this.tasks.splice(index, 1);
      this.tasks = this.tasks.slice(); 
    },
    setActive(data){
      this.activeLink = data;
    }
  },

  mounted() {
    console.log(this.tasks);
    console.log(this.active_tasks);
  },
};
</script>
