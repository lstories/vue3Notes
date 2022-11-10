<template>
  <h2>当前x的值是 {{x}}</h2>
  <button @click="x++">点我x+1</button>

  <hr>
  <h2>当前x的值是 {{x1.y}}</h2>
  <button @click="x={y:888}">点我x+1</button>

  <hr>
  <h2>当前x的值是 {{x1.y}}</h2>
  <button @click="x={y:888}">点我x+1</button>

  <hr>
  <h2>{{person}}</h2>
  <h2>姓名: {{ name }}</h2>
  <h2>年龄: {{ age }}</h2>
  <h2>薪资: {{ job.j1.salary }}K</h2>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="job.j1.salary++">涨薪</button>
</template>

<script>
import { reactive, toRef, toRefs, shallowReactive, shallowRef } from "vue";
export default {
  name: "Demo",
  setup() {
    // 数据
    // shallowReactive 浅层次的响应式, 只考虑第一层的响应式
    // let person = shallowReactive({
    let person = reactive({
      name: "张三",
      age: 19,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    // 基本类型, 与ref无异, 但是对于对象类型的话, 就有所区别
    let x = shallowRef(0)

    // 当在处理对象类型的数据时, shallowRef不对对象类型进行处理, 而, ref会对其进行处理
    let x1 = shallowRef({
      y: 0
    })
    let x2 = ref({
      y: 0
    })
    console.log('@@@', x1)
    console.log('@@@', x2)
    return {
	x,x1,x2,
      // toRefs应用
      ...toRefs(person)

    };
  },


};
</script>

<style>
</style>