<template>
    <h3>我是app组件</h3>
    
</template>

<script>
import { reactive, ref, toRefs, readonly, isRef, isReactive, isReadonly, isProxy } from 'vue';
import Child from "./components/Child.vue"
export default {
  name: "App",
  components: {Child},
  setup(){
    let car = reactive({ name: "奔驰", price: '20w', })
    let sum = ref(0)
    let car2 = readonly(car)

    console.loge(isRef(sum))
    console.loge(isReactive(car))
    console.loge(isReadonly(car2))
    console.loge(isProxy(car))
    console.loge(isProxy(sum))

    return{ ...toRefs(car) }
  }
};
</script>

<style>

</style>