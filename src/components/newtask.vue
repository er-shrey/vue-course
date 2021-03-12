<template>
    <form @submit.prevent="addtodo()" class="col-12 col-lg-6">
        <input v-model="newtaskname" placeholder="Add New Task" type="text" class="form-control" />
    </form>
</template>

<script>
export default {
    name: "newtask",
    data() {
        return {
            newtaskname: ""
        }
    },
    methods: {
        addtodo() {
            if(this.newtaskname.length > 0) {
                this.$emit("on-new-task", this.newtaskname);
            }
            this.newtaskname = '';
        }
    }
}
</script>

<style scoped>

</style>