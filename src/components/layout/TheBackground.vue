<template>
  <div class="h-full w-full absolute top-0 -z-10" :class="color" >
  <img class="w-full h-1/3" :src="bgSrc">
</div>
</template>

<script>
export default {
  props: {
    bgSrc: {
      type: String,
      required: true,
    },
    color: {
      type: String,
      required: false
    }
  },
};
</script>
