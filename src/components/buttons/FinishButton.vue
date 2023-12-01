<template>
  <button>
    <complete-icon v-if="isCompleted === true"></complete-icon>
    <empty-icon v-else></empty-icon>
    </button>
</template>

<script>
import EmptyIcon from "../icons/EmptyIcon.vue";
import CompleteIcon from "../icons/CompleteIcon.vue";

export default {
  components: {
    EmptyIcon,
    CompleteIcon,
  },
  props: {
    isCompleted: {
      type: Boolean,
      required: false,
      default() {
        return false;
      },
    },
  },
};
</script>
