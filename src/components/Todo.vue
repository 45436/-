<template>
    <div class="ui centered card">
        <div class="content" v-show="!isEditing">
            <div class="header">
                {{ todo.title }}
            </div>
            <div class="meta">
                {{ todo.project }}
            </div>
            <div class="extra content">
                <span class="right floated edit icon item" @click="isEditing=true">
                    <i class="edit link icon"></i>
                </span>
                <span class="right floated trash icon" @click="deleteTodo(todo)">
                    <i class="trash link icon"></i>
                </span>
            </div>
        </div>
        <div class="conent" v-show="isEditing">
            <div class="ui form">
                <div class="field">
                    <label>标题</label>
                    <input type="text" v-model="todo.title" />
                </div>
                <div class="field">
                    <label>项目</label>
                    <input type="text" v-model="todo.project" />
                </div>
                <div class="ui two button attached buttons">
                    <button class="ui basic blue button" @click="isEditing=false">
                        关闭
                    </button>
                </div>
            </div>
        </div>
        <div class="ui bottom attached green basic button" @click="deleteTodo(todo)" v-show="!isEditing && todo.done">
            已完成
        </div>
        <div class="ui bottom attached red basic button" @click="todo.done=true;" v-show="!isEditing && !todo.done">
            未完成
        </div>
    </div>
</template>

<script>
export default {
    props: ['todo'],
    data () {
        return {
            isEditing: false
        };
    },
    methods: {
        deleteTodo (todo) {
            this.$emit('delete-todo', todo);
        }
    }
}
</script>

<style scoped>

</style>