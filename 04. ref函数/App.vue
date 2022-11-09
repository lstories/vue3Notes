<template>
  <!-- vue3可以没有跟标签 -->
  <h1>一个人的信息</h1>
  <h2>姓名: {{ name }}</h2>
  <h2>年龄: {{ age }}</h2>
  <h3>工作种类: {{ job.type }}</h3>
  <h3>工作薪水: {{ job.salary }}</h3>
  <button @click="changeInfo">修改人的信息</button>
</template>

<script>
import { ref } from "vue";
export default {
  name: "App",

  setup() {
    // 数据
    let name = ref("张三");
    let age = ref(18);
    let job = ref({
      type: "前端工程师",
      salary: "30k",
    });

    function changeInfo() {
      // name.value = "李四"
      // age.value = 19
      // console.log(name, age);

      job.value.type = 'UI工程师'
      job.value.salary = '20k'
    }

    // 返回一个对象(常用)
    return {
      name,
      age,
      job,
      changeInfo,
    };
  },
};
</script>

<style>
</style>
