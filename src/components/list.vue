<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <p class="display-3">Task List</p>
            </div>
        </div>
        <div class="row">
            <newtask
                @on-new-task="addtodo($event)"
            ></newtask>
        </div>
        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <itask v-for="(task, index) in todos"
                        :key="index"
                        :taskname="task.task"
                        :completed="task.completed"
                        @on-delete="deletetodo(task)"
                        @on-toggle="toggletodo(task)"
                        @on-edit="edittodo(task, $event)"
                    ></itask>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
import itask from "./task"
import newtask from "./newtask"
export default {
    name: "list",
    components: {
        itask,
        newtask
    },
    data() {
        return {
            todos: [
                {
                    task: "Task 1",
                    completed: false
                },
                {
                    task: "Task 2",
                    completed: true
                },
                {
                    task: "Task 3",
                    completed: false
                },
                {
                    task: "Task 4",
                    completed: false
                },
            ]
        }
    },
    methods: {
        addtodo(newtodo) {
            this.todos.push({
                task: newtodo, completed: false
            });
        },
        toggletodo(todo) {
            todo.completed = !todo.completed;
        },
        edittodo(todo, newtodotask) {
            todo.task = newtodotask;
        },
        deletetodo(deletetodo) {
            this.todos = this.todos.filter(
                todo => todo.task != deletetodo.task
            );
        }
    }
}
</script>

<style>

</style>