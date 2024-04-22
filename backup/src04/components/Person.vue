<template>
    <div class="person">
        <h2>姓名：{{ name }}</h2>
        <h2>年龄：{{ age }}</h2>
        <button @click="updateName">修改名字</button>
        <button @click="updateAge">修改年龄</button>
        <button @click="showTel">查看联系方式</button>
    </div>
</template>

<script lang="ts">
export default {
    name: 'Person', // 组件名
    beforeCreate(){
        console.log("beforeCreate...");
    },
    setup() {
        // setup在beforeCreate之前执行
        console.log("setup...");
        // setup函数中this是undefined
        console.log('@@', this);
        // 数据   注意此时的数据并不是响应式的
        let name = '张三'
        let age = 30
        let tel = 18500000000
        
        // 方法
        function updateName() {
            // 修改的是局部变量  不是响应式的  不会影响页面数据变更
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

        // 返回
        // return {name: name, age: age}
        return {name, age, updateName, updateAge, showTel}
    }
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