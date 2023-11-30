<template>
  <the-background :bgSrc="setBgImg" :color="setBgColor"></the-background>
  <main class="flex flex-col w-1/3">
    <div class="flex justify-between">
      <the-title
        title="T O D O"
        options="text-4xl font-bold tracking-wide"
      ></the-title>
      <darkmode-button @toggle-darkmode="setDarkMode"  :darkMode="darkMode"></darkmode-button>
    </div>
  </main>
</template>

<script>
import TheBackground from "./components/TheBackground.vue";
import TheTitle from "./components/TheTitle.vue";
import DarkmodeButton from "./components/buttons/DarkmodeButton.vue";

import bg_desktop_dark from "./assets/images/bg-desktop-dark.jpg";
import bg_desktop_light from "./assets/images/bg-deDsktop-light.jpg";

export default {
  components: {
    TheBackground,
    TheTitle,
    DarkmodeButton,
  },
  data() {
    return {
      bg_desktop_dark,
      bg_desktop_light,
      darkMode: true,
    };
  },
  computed: {
    setBgColor() {
      return this.darkMode ? "bg-[#25273C]" : "bg-[#ffffff]";
    },
    setBgImg() {
      return this.darkMode ? bg_desktop_dark : bg_desktop_light;
    },
  },
  methods: {
    setDarkMode() {
      this.darkMode = !this.darkMode;
    }
  }
};
</script>
