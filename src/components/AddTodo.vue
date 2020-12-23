<template>
    <div class="ui centered card">
        <div class="ui bottom attached blue basic button" @click="showCard=true" v-show="!showCard">
            新增
        </div>

        <div class="conent" v-show="showCard">
            <div class="ui form">
                <div class="field">
                    标题
                    <input type="text" v-model="title" />
                </div>
                <div class="field">
                    项目
                    <input type="text" v-model="project" />
                </div>
                <div class="ui bottom attached blue basic button" @click="addTodo">
                    新增
                </div>
                <div class="ui bottom attached orange basic button" @click="closeCard">
                    关闭
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data(){
        return {
            title:'',
            project:'',
            showCard: false
        }
    },
    methods:{
        closeCard(){
            this.showCard=false;
            this.title='';
            this.project='';
        },
        addTodo(){
            let todo={
                title:this.title,
                project:this.project,
                done:false
            }
            this.$emit("addTodo",todo);
            this.closeCard();
        }
    }
}
</script>
<style scoped>

</style>