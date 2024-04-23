<template>
    <div class="person">
        <h2>汽车信息：品牌：{{ car.brand }}, 价格：{{ car.price }}万</h2>
        <button @click="changePrice">更改价格</button>
        <button @click="changeCar">更改汽车信息</button>
        <br>

        <h2>游戏信息：</h2>
        <ul>
            <li v-for="game in games" :key="game.id">{{ game.name }}</li>
        </ul>
        <button @click="changeFirstGame">修改第一个游戏名字</button>
        <hr>

        <h2>X:{{ obj.x }}, Y:{{ obj.y }}</h2>
        <button @click="incrX">x++</button>
        <button @click="incrY">y++</button>
        <button @click="changeObj">替换</button>
    </div>
</template>

<script lang="ts" setup name="Person">
import { ref, reactive } from 'vue'

// ref既可以定义基本类型 也可以定义对象类型
let car = ref({
    brand: '思域',
    price: 14
})

// 响应式JSON数组
let games = ref([
    { id: '01', name: 'LOL' },
    { id: '02', name: '吃鸡' },
    { id: '03', name: '原神' }
])

let obj = reactive({x:100, y:200})

console.log(car)  // RefImpl底层处理对象类型响应式用的也是Proxy对象  
console.log(obj)  // Proxy对象

function changePrice() {
    car.value.price += 1;
}

function changeCar(){
    // 整个对象替换并不会失去响应式   区别于reactive
    car.value = {brand:'宝马', price:20}
}

function changeFirstGame() {
    games.value[0].name = "英雄联盟"
}

function incrX(){
    obj.x += 1
}

function incrY(){
    obj.y += 1
}

function changeObj(){
    // 重新分配数据会导致失去响应式
    // obj = {x:200, y:300}
    // 这种方式不会失去响应式
    Object.assign(obj, {x:200, y:300})
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