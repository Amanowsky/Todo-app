<template>

<EmptyIcon class="flex justify-center cursor-pointer items-center bg-gradient-to-r from-blue-400 to-purple-600" hover="false"><check-icon></check-icon></EmptyIcon>



</template>

<script>
import EmptyIcon from './EmptyIcon.vue';
import CheckIcon from './CheckIcon.vue';

export default{
    components: {
        EmptyIcon,
        CheckIcon,
    },

}

</script>