<template>
  <h1>个人信息</h1>
  <h2>姓名：{{ person.name }}</h2>
  <h2>年龄：{{ person.age }}</h2>
  <button @click="handleTest">测试EMIT</button>
</template>

<script>
import { reactive } from 'vue'

export default {
  name: 'Demo',
  props: ['msg', 'school'],
  emits: ['hello'],
  setup(props, context) {
    console.log('----setup----', props, context)
    // 数据
    let person = reactive({
      name: '张三',
      age: 24
    })

    // 方法
    function handleTest() {
      context.emit('hello', 666)
    }

    // 返回一个对象
    return {
      person,
      handleTest
    }
  },
  beforeCreate() {
    console.log('----beforeCreate----')
  }
}
</script>
