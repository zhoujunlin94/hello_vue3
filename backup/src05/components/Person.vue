<template>
    <div class="person">
        <h2>姓名：{{ name }}</h2>
        <h2>年龄：{{ age }}</h2>
        <button @click="updateName">修改名字</button>
        <button @click="updateAge">修改年龄</button>
        <button @click="showTel">查看联系方式</button>
        <hr>
        <h2>测试1：{{ a }}</h2>
        <h2>测试2：{{ c }}</h2>
        <button @click="b">测试</button>
    </div>
</template>

<script lang="ts">
export default {
    name: 'Person',
    beforeCreate() {
        console.log("beforeCreate...");
    },
    data(){
        return {
            a: 100,
            // setup生命周期比data早  所以这里能读取到setup中的数据   反之：setup中不能读取data中的数据
            c: this.name
        }
    },
    methods:{
        b(){
            console.log("1111");
        }
    },
    setup() {
        console.log("setup...");
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

        // setup返回值可以直接是数据
        // return function(){
        //     return "哈哈"
        // }

        // return ()=>{
        //     return "哈哈1"
        // }

        //return () => "哈哈2"

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