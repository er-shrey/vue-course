<template>
    <li class="d-flex align-items-center list-group-item">
        <button
            v-if="!isEditing"
            :class="{completed}"
            @click="$emit('on-toggle')"
            class="btn border-0 text-left flex-grow-1"
            @contextmenu.prevent="$emit('on-delete')"
        >
            {{taskname}}
        </button>
        <form v-else @submit.prevent="endEditing()" class="flex-grow-1">
            <input @blur="startEditing()" v-model="newTaskName" type="text" class="form-control" />
        </form>
        <button @click="startEditing()" class="btn btn-outline-primary mr-2">
            <i class="fa fa-pencil" aria-hidden="true"></i>
        </button>
        <button @click="$emit('on-delete')" class="btn btn-outline-danger">
            <i class="fa fa-trash" aria-hidden="true"></i>
        </button>
    </li>
</template>

<script>
export default {
    name: "itask",
    props: {
        taskname: String,
        completed: Boolean
    },
    data() {
        return {
            isEditing: false,
            newTaskName: String
        }
    },
    methods: {
        startEditing() {
            if (!this.isEditing) {
                this.newTaskName = this.taskname;
                this.isEditing = true;
            } else {
                this.endEditing();
            }
        },
        endEditing() {
            this.isEditing = false;
            this.$emit('on-edit', this.newTaskName)
        }
    }
}
</script>

<style scoped>
    .completed {
        text-decoration: line-through;
    }
</style>>