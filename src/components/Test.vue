<template>
  <div class="test">
    <!--获取数据-->
    <h1>{{title}}</h1>
    <p>{{user.fname}}</p>
    <p v-text="user.lname"></p>

    <!--v-if-->
    <p v-if="showname">{{user.fname}}</p>
    <p v-else>nobody</p>

    <!--v-for-->
    <ul>
      <li v-for="i in items">{{i.title}}</li>
    </ul>

    <!--v-on-->
    <button v-on:click="greet">say Greeting</button>

    <!--键盘事件-->
    <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">

    <hr>
    <!--计算属性 computed-->
    <label for="">fname</label>
    <input type="text" v-model="user.fname">
    <br>
    <label for="">lname</label>
    <input type="text" v-model="user.lname">
    <h3>{{fullname}}</h3>

    <!--props 属性-->
    <h2>{{msg}}</h2>

  </div>
</template>

<script>
  export default {
    name:'test',
    props:{
      msg:{
        type:String,
        default:"默认就是当前这些文字"
      }
    },
    data(){
      return{
        title:'hello vue.js',
        user:{
          fname:'hemiah',
          lname:'Wu'
        },
        showname:false,
        items:[
          {title:"item1"},
          {title:"item2"},
          {title:"item3"},
        ],
        count:0
      }
    },
    methods:{
      greet:function () {
        this.count++;
        console.log('hello world');
        console.log(this.count);
      },
      pressKey:function () {
        console.log('键盘事件');
      },
      enterHit:function () {
        console.log('点击了回车');
      }
    },
    computed:{
      fullname:function () {
        return this.user.fname+"  "+this.user.lname
      }
    }
  }
</script>

<style>

</style>