<template>
<p> {{ tasksAmount }} items left </p>
</template>

<script>
export default{
    props: {
        tasksAmount: {
            type: Number,
            required: true
        }
    }
}

</script>