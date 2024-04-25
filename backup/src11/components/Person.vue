<template>
    <div class="person">
        姓：<input type="text" v-model="firstName" /> <br />
        名：<input type="text" v-model="lastName" /> <br />
        <!-- 不够优雅 -->
        <!-- 全名：{{ firstName.slice(0, 1).toUpperCase()  + firstName.slice(1) }} - {{ lastName }} <br /> -->
        全名（只读）：{{ fullName }}  <br />
        全名（只读）：{{ fullName }}  <br />
        <hr>
        全名：{{ fullName2() }}  <br />
        全名：{{ fullName2() }}  <br />
        <hr>
        全名：{{ fullNameRW }} <br/>
        <button @click="changeFullName()">修改fullName</button>
    </div>
</template>

<script lang="ts" setup name="Person">
import { ref, computed } from 'vue'

let firstName = ref('zhou')
let lastName = ref('junlin')

// 定义fullName为计算属性  也是一个ref对象ComputedRefImpl响应式对象  且是只读的
let fullName = computed(() => {
    // 计算属性有缓存  只计算一次
    console.log(11);
    return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + "-" + lastName.value
})

// 定义fullName为计算属性  也是一个ref对象ComputedRefImpl响应式对象  且是可读可写的
let fullNameRW = computed({
    get(){
        return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + "-" + lastName.value
    },
    set(val){
        console.log('set', val);
        const [s1,s2] = val.split('-')
        firstName.value = s1
        lastName.value = s2
    }
})

function changeFullName(){
    fullNameRW.value = 'li-si'
}


function fullName2(){
    // 用一次调用一次
    console.log(222);
    return firstName.value.slice(0, 1).toUpperCase() + firstName.value.slice(1) + "-" + lastName.value
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