<template>
   <div class="todo-footer">
       <label>
           <input type="checkbox" v-model='isall'/><!--  v-model绑定的是checked的值 -->
       </label>
       <span>
           <span>已完成{{ok}}</span> / 全部{{things.length}}
       </span>
       <button class="btn btn-danger" @click="remove">清除已完成的任务</button>
   </div>
</template>

<script>


export default {
name:'MyFooter',
props:['things','removeok','allchecked'],
computed:{
    ok:{
        get(){
            return this.things.reduce((previousValue,currentValue)=>{
                    return previousValue+(currentValue.done==true ? 1 : 0)
            },0)
        },
    },
    // 全选按钮
    isall:{
        get(){
            return this.ok==this.things.length
        },
        set(newvalue){
            this.allchecked(newvalue)
        }

    }
},
methods:{
    remove(){
        this.removeok()
    }
}

}
</script>

<style scoped>
 /* Footer */
 .todo-footer {
       height: 40px;
       line-height: 40px;
       padding-left: 6px;
       margin-top: 5px;
   }
   .todo-footer label{
       display: inline-block;
       margin-right: 20px;
       cursor: pointer;
   }
   .todo-footer label input{
       position: relative;
       top: 1px;
       vertical-align: middle;
       margin-right: 5px;
   }
 
   .todo-footer button{
       float: right;
       margin-top: 5px;
   }
</style>