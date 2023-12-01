<template>
    <div class="h-5 w-5 border rounded-full border-[#393A4C]" :class="setHover"></div>
</template>


<script>
export default{
    props: {
        hover: {
            type: String,
            required: false,
            default() {
                return "true";
            }
        }
    },
    computed: {
        setHover(){
            return this.hover === "true" ? "hover:border-[#1aed52] cursor-pointer" : "";
        }
    }
}



</script>