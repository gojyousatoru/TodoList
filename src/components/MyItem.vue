<template>        
    <div>
        <input type="checkbox" :checked="todo.done" @change="check">
        <span>{{todo.title}}</span>
        <button @click='deleteItem()'>删除</button>
    </div>
</template>

<script>
export default {
    name:'MyItem',
    props:['todo','checkChange','dItem'],
/*    data(){
        return{
            id:this.todo.id,
        } 
    },*/
    methods:{
        check(){
            this.checkChange(this.todo.id)
        },
        deleteItem(){
            this.dItem(this.todo.id)
        }
    }
}
</script>

<style scoped>
    div{
                background-color:rgb(194, 230, 230);
                display: flex;
                justify-content: space-around;

    }
    span{
        display: inline-block;
        height: 20px;
        width:100px;
        font-size: 10px;
        color: rgb(26, 49, 49);
        line-height: 20px;
        background-color: rgb(232, 240, 240);
    }
    button{
        background-color:rgb(91, 159, 211) ;
        height: 20px;
        font-size: 10px;
        color: rgb(219, 250, 250);
        border-color:rgb(234, 240, 246)
    }
    button:hover{
        background-color:rgb(3, 91, 159) ;
    }
</style>

