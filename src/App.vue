<template>
   <div class="root">
        <div class="todo-container">
            <div class="todo-wrap">
                <MyHeader :addlists='addlists'/>
                <MyList :todos='todos' :deletelists='deletelists' :checklist='checklist'/>
                <MyFooter v-if='todos.length>0' :things='todos' :removeok='removeok' :allchecked='allchecked'/>
            </div>
        </div>
    </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyFooter from './components/MyFooter.vue';
import MyList from './components/MyList.vue';
export default {
name:'App',
data(){
    return {
        todos:JSON.parse(localStorage.getItem('todos')) || []
    }
},
watch:{
    todos:{
deep:true,
handler(value){
    localStorage.setItem('todos',JSON.stringify(value))
}
    }
},
components:{
    MyFooter,
    MyHeader,
    MyList,
},
methods:{
    // 新增数据
    addlists(value){
       this.todos.unshift(value)
    },
    // 删除数据
    deletelists(value){
     this.todos.forEach((item,index)=>{
      if(value==item.id) return this.todos.splice(index,1)
})
    },
    // 是否选择数据
    checklist(value){
        this.todos.forEach((item)=>{
      if(value==item.id) item.done=!item.done
})
    },
    // 清除已经完成的任务
    removeok(){
       this.todos= this.todos.filter((item)=>{
     return item.done==false
})
    },
    // 全选
    allchecked(value){
this.todos.forEach((item)=>{
 return  item.done=value
})
    }

}

}
</script>

<style>
 body{
        background: #fff;
    }
    .btn{
        display: inline-block;
        padding: 4px 12px;
        margin-bottom: 0;
        font-size: 14px;
        line-height: 20px;
        text-align: center;
        vertical-align: middle;
        cursor: pointer;
        box-shadow: inset 0 1px 0 rgba(255,255,255,0.2),0 1px 2px rgba(0, 0, 0, 0.05);
        border-radius: 4px;
    }
 
    .btn-danger{
        color: #fff;
        background-color: #da4f49;
        border: 1px solid #bd362f;
    }
 
    .btn-danger:hover{
        color: #fff;
        background-color: #bd362f;
    }
 
    .btn:focus{
        outline: none;
    }
 
    .todo-container{
        width: 600px;
        margin: 0 auto;
    }
    .todo-container .todo-wrap{
        padding: 10px;
        border:1px solid #ddd;
        border-radius: 5px;
    }
</style>