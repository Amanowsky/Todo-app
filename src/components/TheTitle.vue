<template>
<h1 class="text-white" :class="options">{{ title }}</h1>
</template>


<script>
export default{
    props: {
        title: {
            type: String,
            required: true
        },
        options: {
            type: String,
            required: false
        }
    }
}

</script>

