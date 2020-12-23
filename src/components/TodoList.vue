<template>
    <div>
        <p class="tasks">已完成的任务:{{ todos.filter(todo => { return todo.done === true}).length }}</p>
        <p class="tasks">未完成的任务:{{ todos.filter(todo => { return todo.done === false}).length }}</p>
        <Todo v-for="(todo, index) in todos" :todo="todo" :key="index"
        @delete-todo="deleteTodo"
        ></Todo>
        <AddTodo @addTodo="addTodo" />

    </div>
</template>

<script>
import Todo from './Todo'
import AddTodo from './AddTodo'
export default {
    props: ['todos'],
    components: {
        Todo,
        AddTodo
    },
    methods: {
        deleteTodo (todo) {
            swal({
                title: '确定要删除吗?',
                text: '这项任务将要被永久删除!',
                type: 'warning',
                showCancelButton: true,
                confirmButtonColor: '#DD6B55',
                confirmButtonText: '删除!',
                closeOnConfirm: false
            },
            () => {
                const todoIndex = this.todos.indexOf(todo);
                this.todos.splice(todoIndex, 1);
                swal('删除', '任务已经被删除了', 'success');
            });
        },
        addTodo(todo){
            this.todos.push(todo);
        }
    }
}
</script>

<style scoped>
    .tasks {
        text-align: center;
    }
</style>