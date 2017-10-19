<template>
  <div class="users">
    <h1>users</h1>

    <!--添加用户信息-->
    <form action="" v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="name">
      <input type="text" v-model="newUser.email" placeholder="email">
      <input type="submit" value="add">
    </form>

    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted:user.contacted}">
          {{user.name}}:{{user.email}}
        <button v-on:click="deleteUser(user)">X</button>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name:'users',

    data(){
      return{
        newUser:{},
        users:[
          {
            name:'hma Wu',
            email:'h@wu.com',
            contacted:false
          },
          {
            name:'hma Wu',
            email:'h@wu.com',
            contacted:false
          },
          {
            name:'hma Wu',
            email:'h@wu.com',
            contacted:true
          }
        ]
      }
    },
    methods:{
      addUser:function (e) {
        e.preventDefault();
//        console.log('hello');
        this.users.push({
          name:this.newUser.name,
          email:this.newUser.email,
          contacted:false
        })
      },
//      删除哪一个？？
      deleteUser:function (user) {
        console.log('删除事件');
        this.users.splice(this.users.indexOf(user),1);
      }
    },
    created:function () {
      this.$http.get("http://jsonplaceholder.typicode.com/users")
              .then(function (response) {
                console.log(response);
                this.users = response.body
              });
    }
  }
</script>

<style scoped>
  .contacted{
    text-decoration:line-through;
  }
</style>