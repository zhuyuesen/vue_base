来自腾讯课堂  米斯特吴  vue起步

    基础知识

    简单的用户管理 demo

        展示用户信息
        添加用户信息
        删除用户信息

        选中用户 class 的运用

    vue-router 的使用
        1、安装
            npm i vue-router --save

        2、
        main.js 引入 vue-router 模块、使用中间件 、设置路由 、修改 new Vue 部分 、引入 test users 组件

            import VueRouter from 'vue-router'

            使用中间件
            Vus.use(VueRouter);

            设置路由
            const router = new VueRouter({
              mode:'history',
              base:__dirname,
              routes:[
                {path:'/',component:Users},
                {path:'/test',component:Test},
              ]
            })


            修改 new Vue 部分

            new Vue({
              router,
              template: `
               <div id="app">
               <ul>
                    <li>
                    <router-link to="/">Users</router-link>
                    <router-link to="/test">Test</router-link>
            </li>
               </ul>
               <router-view></router-view>
            </div>
              `,

            }).$mount('#app')


            引入 test users 组件
            import Users from './components/Users'
            import Test from './components/Test'


    使用http
        1、 安装 vue-resource
        npm install vue-resource --save

        重启服务

        2、 main.js 中引入
        import VueResource from 'vue-resource'

        3、使用中间件  （可以使用http请求了）
        Vue.use(VueResource);

        http://jsonplaceholder.typicode.com/  json测试使用地址

        4、在users.vue 中 增加 created
        created:function () {
          this.$http.get("http://jsonplaceholder.typicode.com/users")
                  .then(function (response) {
                    console.log(response);
                    this.users = response.body
                  });
        }