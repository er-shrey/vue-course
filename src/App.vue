<template>
    <div>
        <todoList></todoList>
    </div>
</template>

<script>
import todoList from "./components/list.vue"
export default {
    name: "App",
    components: {
        todoList
    }
}
</script>

<style>

body {
    background-color: #464646 !important;
    color: aliceblue !important;
}

</style>