<template>
  <!-- vue3可以没有跟标签 -->
  <h1>一个人的信息</h1>
  <h2>姓名: {{ name }}</h2>
  <h2>年龄: {{ age }}</h2>
  <h3>工作种类: {{ job.type }}</h3>
  <h3>工作薪水: {{ job.salary }}</h3>
  <h3>测试数据: {{ job.a.b.c }}</h3>
  <h3>爱好: {{ hobby }}</h3>
  <button @click="changeInfo">修改人的信息</button>

  <hr />

  <h1>一个人的信息</h1>
  <h2>姓名: {{ person.name }}</h2>
  <h2>年龄: {{ person.age }}</h2>
  <h3>工作种类: {{ person.job.type }}</h3>
  <h3>工作薪水: {{ person.job.salary }}</h3>
  <h3>测试数据: {{ person.job.a.b.c }}</h3>
  <h3>爱好: {{ person.hobby }}</h3>
  <button @click="changeInfo2">修改人的信息</button>

</template>

<script>
import { ref, reactive } from "vue";
export default {
  name: "App",

  setup() {
    // 数据
    let name = ref("张三");
    let age = ref(18);
    let hobby = reactive(["抽烟", "喝酒", "汽车"]);
    let job = reactive({
      type: "前端工程师",
      salary: "30k",
      a: {
        b: {
          c: 666,
        },
      },
    });

    let person = reactive({
      name: "张三",
      age: 18,
      hobby: ["抽烟", "喝酒", "汽车"],
      job: {
        type: "前端工程师",
        salary: "30k",
        a: {
          b: {
            c: 666,
          },
        },
      },
    });

    function changeInfo() {
      name.value = "李四"
      age.value = 19
      console.log(name, age);
      job.type = "UI工程师";
      job.salary = "20k";
      job.a.b.c = 888;
      hobby[0] = "学习";
    }

    function changeInfo2() {
      person.name = "李四"
      person.age = 19
      person.job.type = "UI工程师";
      person.job.salary = "20k";
      person.job.a.b.c = 111;
      person.hobby[0] = "美女";
    }

    // 返回一个对象(常用)
    return {
      name,
      age,
      job,
      hobby,
      person,
      changeInfo,
      changeInfo2,
    };
  },
};
</script>

<style>
</style>
