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
    // vue2中的配置式写法
    data() {
        return {
            name: '张三',
            age: 30,
            tel: 18500000000
        }
    }, // 数据
    methods: {
        updateName() {
            this.name = 'zhang-san'
        },
        updateAge() {
            this.age += 1
        },
        showTel() {
            alert(this.tel)
        }
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