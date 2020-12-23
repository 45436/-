<template>
    <div>
        <p class="tasks">已完成的任务:{{ todos.filter(todo => { return todo.done === true}).length }}</p>
        <p class="tasks">未完成的任务:{{ todos.filter(todo => { return todo.done === false}).length }}</p>
        <div class="ui centered card" v-for="(todo, index) in todos"
        :key="index">
            <div class="header">
                {{ todo.title }}
            </div>
            <div class="meta">
                {{ todo.project }}
            </div>
            <div class="extra content">
                <span class="right floated edit icon">
                    <i class="edit icon"></i>
                </span>
            </div>
            <div class="ui bottom attached green basic button" v-show="todo.done">
                已完成
            </div>
            <div class="ui bottom attached red basic button" v-show="!todo.done">
                未完成
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['todos']
}
</script>

<style scoped>
    .tasks {
        text-align: center;
    }
</style>