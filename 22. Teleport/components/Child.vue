<template>
  <div class="child">
    <h3>我是Son组件</h3>
  </div>
</template>

<script>
import Son from "./Son.vue"
import { inject } from "vue";
export default {
  name: "Child",
  components: {Son},

}
</script>

<style>
.app{
  background-color: skyblue;
  padding: 10px;
}
</style>