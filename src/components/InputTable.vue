<template>
  <div class="main-input-table">
    <!-- <input class="input-class" type="text" /> -->
    <InputBlock :changeData="changeData" />
    <div class="btn-gr">
      <button @click="commit" class="btn">add</button><br />
      <button @click="confirm(data)" class="btn conf">confirm</button><br />
    </div>
    <div class="main-table">
      <p class="block-info" v-bind:key="i" v-for="(el, i) in data">
        {{ data[i] }}
      </p>
    </div>
  </div>
</template>

<script>
import InputBlock from "./Input.vue";
export default {
  name: "InputTable",
  components: {
    InputBlock,
  },
  props: ["changeData", "data", "confirm", "commit"],
};
</script>

<style scoped>
.main-input-table {
  width: 60%;
}
.main-table {
  text-align: center;
  width: 100%;
  padding: 0 34%;
  height: 100px;
}
.block-info {
  font-size: 17px;
  background: grey;
  width: 30%;
  height: 15px;
  padding: 12px;
  margin-bottom: 0px;
  margin-top: 4px;
}
.btn {
  width: 16%;
}
.btn-gr {
  justify-content: center;
  display: flex;
}
</style>
