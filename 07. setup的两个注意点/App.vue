<template>
  <Demo @hello="showHelloMsg" msg="你好啊" school="东莞城市">
    <template v-slot:qwe>
      <span>尚硅谷</span>
    </template>
    
  </Demo>
</template>

<script>
import Demo from './components/Demo.vue'
export default {
  name: 'App',
  components: {Demo},
  setup() {
    function showHelloMsg(value){
      alert(`你好啊, 我触发了hello事件, 收到的参数是: ${value}`)
    }


    return {
      showHelloMsg
    }
  }
}
</script>

<style>

</style>