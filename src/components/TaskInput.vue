<template>
<main-box>
<empty-icon hover="false"></empty-icon>
<input v-model="text" @keyup.enter="submit" class="ml-5 w-full bg-transparent text-[#CACDE8] focus:outline-none" type="text" placeholder="Create a new todo.. ">
</main-box>
</template>

<script>
import EmptyIcon from "./icons/EmptyIcon.vue"
import MainBox from "./layout/MainBox.vue";

export default{
    components: {
        EmptyIcon,
        MainBox
    },
    emits: ['task-added'],
    data() {
        return {
            text: ""
        }
    },
    methods: {
        submit(){
            this.$emit('task-added',this.text);
            this.text = ""
        }
    }
}


</script>