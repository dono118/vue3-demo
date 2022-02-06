<template>
  <h1>个人信息</h1>
  <h2 v-show="person.name">姓名：{{person.name}}</h2>
  <h2>年龄：{{person.age}}</h2>
  <h2 v-show="person.sex">性别：{{person.sex}}</h2>
  <h2>职位：{{person.job.type}}</h2>
  <h2>薪水：{{person.job.salary}}</h2>
  <h2>爱好：{{person.hobbies}}</h2>
  <h2>测试数据c：{{person.job.a.b.c}}</h2>
  <button @click="changeInfo">修改个人信息</button>
  <button @click="addSex">添加sex属性</button>
  <button @click="deleteName">删除name属性</button>
</template>

<script>
import { reactive } from "vue";

export default {
  name: 'App',
  setup() {
    // 数据
    let person = reactive({
      name: '张三',
      age: 24,
      job: {
        type: '前端工程师',
        salary: '10k',
        a: {
          b: {
            c: 666
          }
        }
      },
      hobbies: ['抽烟', '喝酒', '烫头']
    })


    // 方法
    function changeInfo() {
      person.name = '李四'
      person.age = 28
      // console.log(job);
      person.job.a.b.c = 999
      person.job.type = 'UI设计师'
      person.job.salary = '20k'
      person.hobbies[0] = '学习'
    }

    function addSex() {
      person.sex = '男'
    }

    function deleteName() {
      delete person.name
    }

    // 返回一个对象
    return {
      person,
      changeInfo,
      addSex,
      deleteName
    }
  }
}
</script>
