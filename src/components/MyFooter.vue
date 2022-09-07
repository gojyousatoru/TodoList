<template>
  <div id='MyFooter'>
    <input type="checkbox" :checked='checked' @change='checkChange'>
    <label>
        已完成{{haveDone}}/全部{{total}}
    </label>
    <button @click='deleteAllTodo'>清除</button>
  </div>
</template>

<script>
export default{
    name:'MyFooter',
    props:['todos','checkTotal'],
    computed:{
        haveDone(){
            let i = 0
            this.todos.forEach((todo)=>{
                if(todo.done == true) i++
            })
            return i
        },
        total(){
            return this.todos.length
        },
        checked(){
            return this.haveDone == this.total && this.total>0}
    },
    methods:{
            /*checkChange(e){
            (e.target.checked == true)?this.checkTotal(true)
            :this.checkTotal(false)
        }*/
        checkChange(){
            this.$emit('checkTotal',this.checked?0:1)
        },
        deleteAllTodo(){this.$emit('deleteAllTodo')}
    }
}
</script>

<style scoped>
 #MyFooter{
    display:flex ;
    justify-content: space-around;
    }
div{
     background-color:rgb(194, 207, 230);
     display: flex;
     justify-content: space-around;
    }
label{
    display: inline-block;
    height: 20px;
    width:100px;
    font-size: 10px;
    color: rgb(26, 49, 49);
    line-height: 20px;
    background-color: rgb(233, 232, 240);
}
button{
    background-color:rgb(127, 91, 211) ;
    height: 20px;
    font-size: 10px;
    color: rgb(219, 250, 250);
    border-color:rgb(234, 240, 246)
}    
button:hover{
    background-color:rgb(48, 5, 149) ;

}
</style>