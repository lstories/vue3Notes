<template>
  <input type="text" v-model="keyWord" />
  <h3>{{ keyWord }}</h3>
  <hr />
</template>

<script>
import { ref, customRef } from "vue";
export default {
  name: "App",
  setup() {
    function myRef(value, delay) {
      let timer;
      console.log("---myRef---");
      return customRef((track, trigger) => {
        return {
          get() {
            console.log(`有人从myRef这个容器中读取数据了, 我把${value}给了他`);
            track(); // 通知Vue追踪value的变化, 提取和get说value是有用的
            return value;
          },
          set(newValue) {
            console.log(`有人从myRef这个容器中的数据改为: ${newValue}`);
            clearTimeout(timer);
            timer = setTimeout(() => {
              value = newValue;
              trigger(); // 通知Vue区重新解析模板
            }, delay);
          },
        };
      });
    }

    // let keyWord = ref('hello')  // 使用Vue提供的ref
    let keyWord = myRef("hello", 500); // 使用自定义的ref
    return {
      keyWord,
    };
  },
};
</script>

<style>
</style>