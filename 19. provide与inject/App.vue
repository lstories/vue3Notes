<template>
  <div class="app">
    <h3>我是app组件, {{name}} ---- {{price}}</h3>
    
  </div>
</template>

<script>
import { reactive, toRef, toRefs, provide } from 'vue';
import Child from "./components/Child.vue"
export default {
  name: "App",
  components: {Child},
  setup(){
    let car = reactive({
      name: "奔驰",
      price: '20w',
    })

    provide('car', car) // 给自己的后代组件传递数据

    return{
      ...toRefs(car)
    }
  }
};
</script>

<style>
.app{
  background-color: gray;
  padding: 10px;
}
</style>