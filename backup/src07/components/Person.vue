<template>
    <div class="person">
        <h2>姓名：{{ name }}</h2>
        <h2>年龄：{{ age }}</h2>
        <button @click="updateName">修改名字</button>
        <button @click="updateAge">修改年龄</button>
        <button @click="showTel">查看联系方式</button>
    </div>
</template>

<script lang="ts" setup name="Person">
    import {ref} from 'vue'

    // 数据  响应式数据(基本数据类型)用ref包裹 => RefImpl对象
    let name = ref('张三')
    let age = ref(30)
    let tel = 18500000000
    let address = "上海"

    console.log(1, name);
    console.log(2, age);
    console.log(3, tel);
    console.log(4, address);

    // 方法
    function updateName() {
        // name对象不再是字符串对象而是 RefImpl对象所以需要 .value   模板中的插值表达式不需要.value
        name.value = 'zhang-san'
    }
    function updateAge() {
        age.value += 1
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