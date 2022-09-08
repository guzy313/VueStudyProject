1.环境准备；
    ① 安装node.js
    ② 安装脚手架@vue/cli
      npm install --global vue-cli
      npm config set registry https://registry.npm.taobao.org （有报错需要再执行这个再安装）
      npm install --global vue-cli
2.使用脚手架搭建前端；
   ①  安装完@vue/cli脚手架后，电脑中找个合适的文件路径，在路径下打开cmd窗口执行以下命令，创建vue前端项目：
    npm i -g @vue/cli-init
    //项目名为：spring-boot-vue-frontend
    vue init webpack spring-boot-vue-frontend
   此处执行失败可以执行 set-ExecutionPolicy RemoteSigned 之后再执行
   ② 修改端口 
      在生成的项目config路径下的index.js中，默认为8080
   ③ 运行前端
      在项目根目录(即项目中src目录) 执行命令 npm start
   
3.集成axios模块；
   主要功能：
    从浏览器中创建 XMLHttpRequests；
    从 node.js 创建 http 请求；
    支持 Promise API；
    拦截请求和响应；
    转换请求数据和响应数据；
    取消请求；
    自动转换 JSON 数据；
    客户端支持防御 XSRF
   安装：
    项目根目录下执行命令：
        npm install axios --save-dev

4.添加Element组件库；
    ① 安装Element UI的npm模块
        npm i element-ui -S --save-dev
    ② 将Element UI集成到vue框架内
        修改src/main.js文件：
        修改后
            import Vue from 'vue'
            import App from './App'
            import router from './router'
            import ElementUI from 'element-ui'
            import locale from 'element-ui/lib/locale/lang/en'
            import 'element-ui/lib/theme-chalk/index.css'

            Vue.config.productionTip = false
            Vue.use(ElementUI, { locale })

            /* eslint-disable no-new */
            new Vue({
            el: '#app',
            router,
            components: { App },
            template: '<App/>'
            })
5.使用Element组件库添加元素；
    在这之前，我先在src底下建立几个文件夹：
        views文件夹用于存放功能模块入口.vue文件；
        views文件夹底下创建login文件夹，用于存放login模块的.vue文件；
        utils文件夹用于存放一些工具类；
        api文件夹用于存放前端请求封装（基于axios）
    在src/views/login底下新建index.vue文件，并在文件内写入代码
        <template>
            <div>
                <el-button type="success">Element UI button 1</el-button>
                <el-button type="danger" @click="sayHello">{{ buttonText }}</el-button>
            </div>
        </template>

        <script>
        export default {
            name: "login",
            data() {
                return {
                buttonText: "Element UI button 2",
                };
            },
            created() {
                console.log("This is vue project!");
            },
            methods: {
                sayHello() {
                alert("Hello dylanz!");
                },
            },
            };
        </script>

        <style>
        </style>
    router中指明路由:
        在src/router/index.js文件中声明访问路由即页面的访问路径
        需要添加：
            import login from '@/views/login/index'
            export default new Router({
            routes: [
                {
                path: '/login.html',
                name: 'login',
                component: login
                }
            ]
            })
6.运行vue前端；  
    npm start