<template>
  <div id="app">
    <MyHeader :addTodo="addTodo"/>
    <MyList :todos='todos'  />
    <MyFooter :todos="todos" @checkTotal='checkTotal' @deleteAllTodo='deleteAllTodo'/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyList from './components/MyList.vue'
import MyFooter from './components/MyFooter.vue'

export default{
  name: 'App',
  data(){
    return{
      todos:JSON.parse(localStorage.getItem('Todos')) || []
      }
  },
  components: {
    MyHeader,
    MyList,
    MyFooter
  },
  watch:{
    todos:{
      deep:true,
      handler(val){
        localStorage.setItem('Todos',JSON.stringify(val))
      }
    }
  },
  methods:{
    addTodo(todo){
      this.todos.unshift(todo)
    },
    dItem(id){
      this.todos = this.todos.filter((t)=>{
        return t.id != id
      })
    },
    checkChange(id){
      this.todos.forEach((value)=>{
        if(value.id==id) value.done = !value.done
        }
      )
    },
    checkTotal(bool){
      this.todos.forEach((todo)=>{todo.done=bool})
    },
    deleteAllTodo(){
      this.todos = []
    }
  },
  mounted(){
    this.$bus.$on('check',(todo)=>{this.checkChange(todo)})
    this.$bus.$on('dItem',this.dItem)
  
}}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
