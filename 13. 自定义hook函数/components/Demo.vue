<template>
  <hr />
  <h2>当前求和为 : {{ sum }}</h2>
  <button @click="sum++">点我+1</button>
  <hr />
  <h2>当前点击鼠标的坐标为: x : {{point.x}}  , y : {{point.y}} </h2>
</template>

<script>
import { userInfo } from "os";
import { reactive, watch, ref, watchEffect } from "vue";
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";
import usePoint from '../hooks/usePoint.js'
export default {
  name: "Demo",
  setup() {
    // 数据
    let sum = ref(0);

    let point = usePoint()


    // 返回一个对象(常用)
    return {
      sum,
      point,
    };
  },




};
</script>

<style>
</style>