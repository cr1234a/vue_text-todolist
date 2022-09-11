<template>
  <div>
       <li>
        <label>
            <input type="checkbox" :checked='items.done' @change='check' :id="items.id"/>
            <span>{{items.content}}</span>
        </label>
        <button class="btn btn-danger" @click="deletelist" :id="items.id">删除</button>
       </li>
   </div>
</template>

<script>
export default {
name:'MyItem',
props:['items','deletelists','checklist'],
methods:{
    // 删除数据
    deletelist(e){
       this.deletelists(e.target.id)
    },
    // 选择与不选择
    check(e){
        this.checklist(e.target.id)
    }
}
}

</script>

<style scoped>
li{
       list-style: none;
       height: 36px;
       line-height: 36px;
       padding: 0 5px;
       border-bottom: 1px solid #ddd;
   }
   li label{
       float:left;
       cursor: pointer;
   }
 
   li label li input{
       vertical-align: middle;
       margin-right: 6px;
       position: relative;
       top: -1px;
   }
 
   li button{
       float: right;
       display: none;
       margin-top: 3px;
   }
 
   li:before{
       content: initial;
   }
   li:last-child{
       border-bottom: none;
   }
   li:hover button{
display:block
   }
</style>