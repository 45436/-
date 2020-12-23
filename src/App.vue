<template>
  <div>
    <TodoList :todos="todos"></TodoList>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
import TodoList from './components/TodoList'

export default {
  components: {
    TodoList
  },
  data () {
    return {
      todos: [{
        title: '任务1',
        project: '待办事项A',
        done: false
      }, {
        title: '任务2',
        project: '待办事项B',
        done: true
      }, {
        title: '任务3',
        project: '待办事项C',
        done: false
      }]
    };
  }
}
</script>

<style>

</style>
