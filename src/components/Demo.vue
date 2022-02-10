<template>
  <h1>个人信息</h1>
  姓：<input type="text" v-model="person.firstName" /><br>
  名：<input type="text" v-model="person.lastName" /><br>
  全名：<input type="text" v-model="person.fullName" />
  <!-- <h2>全名：{{ person.fullName }}</h2> -->
  <h2>年龄：{{ person.age }}</h2>
  <button @click="handleTest">测试EMIT</button>
</template>

<script>
import { reactive, computed } from 'vue'

export default {
  name: 'Demo',
  props: ['msg', 'school'],
  emits: ['hello'],
  setup(props, context) {
    // console.log('----setup----', props, context)
    console.log('----setup----', props, context.slots)
    // 数据
    let person = reactive({
      // name: '张三',
      age: 24,
      firstName: '',
      lastName: ''
    })

    // 计算属性（简写）
    /* person.fullName = computed(() => {
      return person.firstName + person.lastName
    }) */
    // 计算属性（完整写法）
    person.fullName = computed({
      get() {
        return person.firstName + '-' + person.lastName
      },
      set(value) {
        const nameArr = value.split('-')
        person.firstName = nameArr[0]
        person.lastName = nameArr[1]
      }
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
