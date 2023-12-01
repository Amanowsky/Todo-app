<template>

    <div class="w-full p-4 flex items-center rounded-sm" :class="setDarkMode">
        <slot></slot>
    </div>
</template>


<script>
export default{

    props: {
        isDarkMode: {
            type: Boolean,
            required: true,
        }
    },
    computed: {
        setDarkMode() {
            return this.isDarkMode === false ? "bg-[#FAFAFA]" : "bg-[#25273C]";
        }
    }
}


</script>

