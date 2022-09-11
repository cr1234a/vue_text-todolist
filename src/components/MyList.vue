<template>
    <ul class="todo-main">
        <!-- 渲染数据 -->
        <MyItem v-for='item in todos' :key='item.id' :items='item' :deletelists='deletelists' :checklist='checklist'/>
    </ul>
</template>

<script>
import MyItem from './MyItem.vue'   
export default {
name:'MyList',
components:{
    MyItem
},
props:['todos','deletelists','checklist']
}
</script>

<style>
  .todo-main{
       margin-left: 0px;
       border: 1px solid #ddd;
       border-radius: 2px;
       padding: 0px;
   }
 
   .todo-empty{
       height: 40px;
       line-height: 40px;
       border: 1px solid #ddd;
       border-radius: 2px;
       padding-left:5px;
       margin-top: 10px;
   }
</style>