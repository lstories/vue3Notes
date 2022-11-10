<template>
  <hr />
  <h2>当前求和为 : {{ sum }}</h2>
  <button @click="sum++">点我+1</button>
  <hr />
  <h2>当前的信息为: {{ msg }}</h2>
  <button @click="msg += '!'">修改信息</button>
  <hr />
  <h2>姓名: {{ person.name }}</h2>
  <h2>年龄: {{ person.age }}</h2>
  <h2>薪资: {{ person.job.j1.salary }}K</h2>
  <button @click="person.name += '~'">修改姓名</button>
  <button @click="person.age++">增长年龄</button>
  <button @click="person.job.j1.salary += 20">涨薪</button>
</template>

<script>
import { reactive, watch, ref } from "vue";
export default {
  name: "Demo",
  setup() {
    // 数据
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = ref({
      name: "张三",
      age: 19,
      job: {
        j1: {
          salary: 20,
        },
      },
    });
    // 监视

    console.log(person)

    watch(sum, (newValue,oldValue)=>{
      console.log('sum变了',newValue, oldValue)
    })

    // 第一种方法, 监测的不再是ref里面的数据了, 而是求助于reactive中的Proxy对象
    watch(person.value, (newValue,oldValue)=>{
      console.log('person变了',newValue, oldValue)
    })
    
    // 第二种方法
    watch(person, (newValue,oldValue)=>{
      console.log('person变了',newValue, oldValue)
    },{deep:true})




    // 返回一个对象(常用)
    return {
      sum,msg,person
    };
  },

  /*
  watch: {
    // Vue2简写
    // sum(newValue, oldValue) {
    //   console.log('sum的值变化了', newValue, oldValue)
    // }

    // Vue2完整写法
    sum:{
      immediate:true,
      deep: true,
      handler(newValue, oldValue){
        console.log('sum的值变化了', newValue, oldValue)
      }
    }
  },
   */
};
</script>

<style>
</style>