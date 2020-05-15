<template>
  <div id="app" class="app">
    <!--    <img alt="Vue logo" src="./assets/logo.png">-->
    <div class="app__wrapper">
      <Field v-for="item in fieldNames" :key="item" :name="item" />
    </div>
  </div>
</template>

<script>
import Field from "./components/Field";
import { fieldNames } from "./config";

export default {
  name: "App",
  components: {
    Field
  },
  data() {
    return {
      fieldNames: fieldNames
    };
  }
};
</script>

<style lang="scss">
@import "scss/main";
</style>

<!--To do: Add Vue Router, Add Vuex store -->
