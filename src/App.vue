<template>
  <the-background :bgSrc="setBgImg" :color="setBgColor"></the-background>
  <main class="flex flex-col w-1/3 mt-24 ">
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
    <task-input class="shadow-xl" :isDarkMode="darkMode" @task-added="addTasks"></task-input>
    <div v-if="this.tasks.length !== 0" class="shadow-xl">
    <div class="mt-5">
      <task-area
        @complete-task="completeTast"
        @remove-task="removeTast"
        :activeFilter="activeLink"
        :isDarkMode="darkMode"
        :tasks="tasks"
      ></task-area>
    </div>
    <div class="flex">
      <navi-bar
        v-if="tasks.length !== 0"
        @clear-completed="clearAllCompleted"
        @set-link="setActiveFilter"
        class="text-sm"
        :isDarkMode="darkMode"
        :isActive="activeLink"
        :tasksAmount="setActiveTaskAmount"
      ></navi-bar>
    </div>
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
      activeLink: "all",

      tasks: [],
    };
  },
  computed: {
    setBgColor() {
      return this.darkMode ? "bg-[#161722]" : "bg-[#FAFAFA]";
    },
    setBgImg() {
      return this.darkMode ? bg_desktop_dark : bg_desktop_light;
    },
    setActiveTaskAmount() {
      return this.tasks.filter((el) => el.status === "active").length;
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
        status: "active",
      };
      this.tasks.push(task);
      this.tasks = this.tasks.slice();
    },
    removeTast(task) {
      const index = this.tasks.findIndex((el) => el.id === task);
      this.tasks.splice(index, 1);
      this.tasks = this.tasks.slice();
    },
    completeTast(task) {
      const index = this.tasks.findIndex((el) => el.id === task);
      this.tasks[index].status =
        this.tasks[index].status === "active" ? "complete" : "active";
      this.tasks = this.tasks.slice();
    },
    setActiveFilter(data) {
      this.activeLink = data;
    },
    clearAllCompleted() {
      this.tasks = this.tasks.filter((el) => el.status === "active");
      this.tasks = this.tasks.slice();
    },
  },
};
</script>
