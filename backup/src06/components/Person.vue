<template>
    <div class="person">
        <h2>姓名：{{ name }}</h2>
        <h2>年龄：{{ age }}</h2>
        <button @click="updateName">修改名字</button>
        <button @click="updateAge">修改年龄</button>
        <button @click="showTel">查看联系方式</button>
    </div>
</template>

<!-- <script lang="ts">
    export default {
        // 组件名
        name: 'Person1234'
    }
</script> -->


<!-- 需要安装插件  npm i vite-plugin-vue-setup-extend 并在vite.config.ts文件中注册 -->
<script lang="ts" setup name="Person456">
    // 数据   
    let name = '张三'
    let age = 30
    let tel = 18500000000

    // 方法
    function updateName() {
        name = 'zhang-san'
        console.log("updateName-->", name);
    }
    function updateAge() {
        age += 1
        console.log("updateAge-->", age);
    }
    function showTel() {
        alert(tel)
    }
</script>

<style scoped>
.person {
    background-color: skyblue;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;
}

button {
    margin: 0 5px;
}
</style>