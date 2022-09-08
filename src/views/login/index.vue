<template>
    <div>
        <el-button type="success">button1</el-button>
        <el-button type="danger" @click="sayHello">{{buttonText}}</el-button>
    </div>
</template>
<script>
    export default{
        name:"login",
        data(){
            return{
                buttonText:"测试按钮2"
            };
        },
        created(){
            console.log("这是一个vue项目");
        },
        methods:{
            sayHello(){
                alert("hihihi");
            },
        },
    };
</script>
<style>
</style>