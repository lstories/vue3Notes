<template>
  <h2>当前求和为:  {{sum}}</h2>
  <button @click="sum++">点我++</button>


  <hr>
  <h2>{{person}}</h2>
  <h2>姓名: {{ name }}</h2>
  <h2>年龄: {{ age }}</h2>
  <h2>薪资: {{ job.j1.salary }}K</h2>

  <h3 v-show="person.car">座驾信息: {{person.car}}</h3>
  <button @click="name += '~'">修改姓名</button>
  <button @click="age++">增长年龄</button>
  <button @click="job.j1.salary++">涨薪</button>

  <button @click="showRawPerson">输出最原始的person</button>
  <button @click="addCar">给人添加一台车</button>
  <button @click="person.car.name += '!!'">换车名</button>
  <button @click="changePrice">换价格</button>
</template>




<script>
import { reactive, toRefs, ref, toRaw, markRaw} from "vue";
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

    function showRawPerson(){
      const p = toRaw(person)
      p.age++
      // p不会变化
      console.log(p)
    }

    function addCar(){
      let car = {name: '奔驰', price: 40}
      person.car = markRaw(car)
    }

    function changePrice(){
      person.car.price++
      console.log(person.car.price)
    }

    return {
      sum,
      person,
      // toRefs应用
      ...toRefs(person),
      showRawPerson,
      addCar,
      changePrice
    };
  },


};
</script>

<style>
</style>