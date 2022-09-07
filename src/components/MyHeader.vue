<template>
  <div id="MyHeader">
    <input placeholder="请输入代办事项,回车添加" type="text" v-model="todo" @keyup.enter="add">
  </div>
</template>

<script>
import {nanoid} from 'nanoid'
export default {
  name: 'MyHeader',
  data(){
    return{
      todo:''
    }
  },
  props:['addTodo'],
  methods:{
    add(e){
      let title = e.target.value;
      const todo = {id:nanoid(),title:title,done:false};
      this.addTodo(todo);
      this.todo = '';
    }
  }
}
</script>

<style scoped>
#MyHeader {
  margin:0;
  height:30px;
  background-color: #42b983;
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
