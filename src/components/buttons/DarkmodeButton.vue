<template>
  <button @click="setDarkMode">
    <component :is="setComponent"></component>
    </button>
</template>

<script>
import SunIcon from "../icons/MoonIcon.vue";
import MoonIcon from "../icons/SunIcon.vue";
export default {
  components: {
    SunIcon,
    MoonIcon,
  },
  props: {
    darkMode: {
        type: Boolean,
        required: true,
        default() {
            return true
        }
    }
  },
  computed:{
    setComponent(){
        return this.darkMode ? MoonIcon : SunIcon
    }
  },
  emits: ['toggle-darkmode'],
  methods: {
    setDarkMode() {
      this.$emit('toggle-darkmode');
    }
  }
};
</script>
