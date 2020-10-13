<template>
  <div class="todoList">
    <div class="title">
      <h3>ToDoList</h3>
      <input type="text" @keyup.enter="addNewList" v-model="newlist" />
    </div>

    <div class="toFinsh">
      <h3>待完成</h3>
      <ul>
        <li v-for="(item,index) in toFinshed" :key="index">
          <div>{{index}}、{{item}}</div>
          <div>
              <button class="btn1" @click="finshed(index,item)">已完成</button>
              <button class="btn2">未完成</button>
          </div>
        </li>
      </ul>
    </div>


     <div class="toFinsh">
      <h3>已完成</h3>
      <ul>
        <li v-for="(item,index) in Finshed" :key="index">
          <div>{{index}}、{{item}}</div>
          <div>
              <button class="btn3" @click="deleteList(index)">删除</button>
              <button class="btn4" @click="failFinshed(index,item)">未完成</button>
          </div>
        </li>
      </ul>
    </div>
  
  </div>
</template>
<script>
export default {
  data() {
    return {
      newlist: "",
      toFinshed: ["0000", "xxxxx", "3333"],
      Finshed: ["9999", "8888"],
    };
  },
  methods: {
    //删除
    deleteList(index){
      this.Finshed.splice(index,1);
    },
    //已完成
    finshed(index,item){
        this.toFinshed.splice(index,1)
         if (!this.Finshed.includes(item)) {
        this.Finshed.push(item);
      }
    },
    //未完成
    failFinshed(index,item){
        this.Finshed.splice(index,1)
       if (!this.toFinshed.includes(item)) {
        this.toFinshed.push(item);
      }
    },
    addNewList() {
      if (this.newlist && !this.toFinshed.includes(this.newlist)) {
        this.toFinshed.push(this.newlist);
      }
    },
  },
};
</script>
<style lang="less" scoped>
* {
    margin: 0;
    padding: 0;
}
ul li{
  list-style: none;
}
image{
  display: block;
}
.todoList {
  width: 40%;
  padding: 20px;
  margin: 0 auto;
  border: 1px solid red;
  .title{
    display: flex;
    margin-bottom: 20px;
    input{
      margin-left: 30px;
    }
  }
  .toFinsh{
    margin-bottom: 40px;
    ul{
      display: flex;
      flex-direction: column;
      li{
        display: flex;
        align-items: center;
        margin: 4px;
        div:first-child{
          margin-right: 20px;
        }
      }
    }
    .btn1,.btn2,.btn3,.btn4{
      width: 80px;
      height: 40px;
      line-height: 40px;
      text-align: center;
      border: 0;
      margin-right: 10px;
      border-radius: 8px;
      color: white;
    }
    .btn1{
      background-color: green;
    }
    .btn2{
      background-color: hotpink;
    }
    .btn3{
      background: red;
    }
    .btn4{
      background: orange;

    }
  }
}
</style>