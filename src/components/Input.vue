<template>
  <input
    class="input-class"
    v-model="data"
    type="text"
    @change="changeData(data)"
  /><br />
</template>

<script>
export default {
  name: "InputBlock",
  props: ["changeData"],
  data() {
    return {
      data: "",
    };
  },
};
</script>

<style>
.input-class {
  margin-bottom: 5px;
  width: 30%;
  padding: 15px;
  font-size: 15px;
  border-radius: 0;
  border: 0;
  background: rgb(187, 187, 187);
}
</style>