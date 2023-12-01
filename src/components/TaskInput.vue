<template>

<main-box :isDarkMode="isDarkMode">
<button><empty-icon hover="false"></empty-icon></button>
<input v-model="text" @keyup.enter="submit" class="ml-5 w-full bg-transparent focus:outline-none" :class="setColor" type="text" placeholder="Create a new todo.. ">

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

    props: {
        isDarkMode: {
            type: Boolean,
            required: true,
        }
    },
    computed: {
        setColor(){
            console.log(this.isDarkMode)
            return this.isDarkMode === true ? "text-[#CACDE8]" : "text-[#484B6A]"
        }
    },
    methods: {
        submit(){
            if(this.text.trim() === "") return;

            this.$emit('task-added',this.text);
            this.text = ""
        }
    }
}


</script>