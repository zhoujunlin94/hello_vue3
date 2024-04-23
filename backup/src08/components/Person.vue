<template>
    <div class="person">
        <h2>汽车信息：品牌：{{ car.brand }}, 价格：{{ car.price }}万</h2>
        <button @click="changePrice">更改价格</button>
        <br>

        <h2>游戏信息：</h2>
        <ul>
            <li v-for="game in games" :key="game.id">{{ game.name }}</li>
        </ul>
        <button @click="changeFirstGame">修改第一个游戏名字</button>
        <hr>

        <h2>测试：{{ obj.a.b.c }}</h2>
        <button @click="changeObj">修改obj</button>
    </div>
</template>

<script lang="ts" setup name="Person">
import { reactive } from 'vue'

// reactive只能定义对象类型响应式数据
// reactive让对象类型数据变成响应式  Proxy对象
let car = reactive({
    brand: '思域',
    price: 14
})

// 响应式JSON数组
let games = reactive([
    { id: '01', name: 'LOL' },
    { id: '02', name: '吃鸡' },
    { id: '03', name: '原神' }
])

// 支持深层次
let obj = reactive({
    a: {
        b: {
            c: 100
        }
    }
})

//console.log(car);

function changePrice() {
    car.price += 1;
}

function changeFirstGame() {
    games[0].name = "英雄联盟"
}

function changeObj() {
    obj.a.b.c += 1
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

li {
    font-size: 20px;
}
</style>