<template>
  <Demo @hello="sayHello" msg="Hi" school="尚硅谷">
    <template #haha>
      <span>哈哈哈</span>
    </template>
  </Demo>
</template>

<script>
import Demo from './components/Demo'

export default {
  name: 'App',
  components: {
    Demo
  },
  setup() {
    function sayHello(data) {
      alert(`子组件触发了hello事件，传递给父组件的参数是：${data}`)
    }
    return {
      sayHello
    }
  }
}
</script>
