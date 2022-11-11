<template>
  <div class="child">
    <h3>我是Son组件(子)</h3>
  </div>
</template>

<script>
import Son from "./components/Son.vue"
import { inject } from "vue";
export default {
  name: "Child",
  components: {Son},
  setup(){
    let x = inject('car')
    console.log(x, 'child')
  }
}
</script>

<style>
.app{
  background-color: skyblue;
  padding: 10px;
}
</style>