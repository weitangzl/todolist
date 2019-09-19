<!--<template>
  <div id="Lead">
    <span>输入待办事项</span>
    <input type="text" v-model="todo" @keydown="add($event)">
    <button @click="add">+</button>
    <div id="List">
      <span>待办事项</span>
      <p>进行中</p>
      <ul>
        <li v-for="(item) in list" v-if="item.checked" >
          <input type="checkbox" v-model="item.checked" >
          <a>{{item.title}}</a>
          <button @click="delet()">删除</button>
        </li>
      </ul>
      <ul>
        <p>已完成</p>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>

</style>-->
<template>
  <div id="app">
         <input type="text"  v-model="todo" ref="pu"/>
         <button @click="add()">+新增</button>
         <br/>
         <br/>
         <div>
           <p>进行中</p>
           <ul>
              <li v-for="(item,key) in checkList">
                {{key+1}} {{item}}   <button v-on:click="remove(key)">完成</button>
                                      <button v-on:click="dele(key)">删除</button>
              </li>
            </ul>
         </div>
         <hr>
         <div>
           <p>已完成</p>
           <ul>
             <li v-for="(item,key) in doneList">
               {{key+1}} {{item}}
             </li>
           </ul>
         </div>
  </div>
  
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      todo:"",
      checkList:[],
      doneList:[]
    }    
  },
  methods:{
      add(){
       var va = this.$refs.pu.value;   
        this.checkList.push(va);
        this.todo = "";
    },
    remove(key){
      var val = this.checkList[key];
      this.doneList.push(val);
      this.checkList.splice(key,1);
    },
    dele(key){
      this.checkList.splice(key,1);
    }
}
}
</script>


<style>


</style>
