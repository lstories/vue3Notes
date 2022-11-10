<template>
  <h2>当前求和为:  {{sum}}</h2>
  <button @click="sum++">点我++</button>


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
import { reactive, toRefs, ref, readonly, shallowReadonly } from "vue";
export default {
  name: "Demo",

  setup() {
    let sum = ref(0)
    let person = reactive({
      name: "张三",
      age: 19,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    // 只读
    person = readonly(person)
    person = shallowReadonly(person)
    
    sum = readonly(sum)
    sum = shallowReadonly(sum)

    return {
      sum,
      // toRefs应用
      ...toRefs(person),

    };
  },


};
</script>

<style>
</style>