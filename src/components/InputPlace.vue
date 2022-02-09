<template>
  <div class="flex">
    <button @click="btn(i)" class="btnTab" v-bind:key="i" v-for="i in count">
      Tab - {{ i }}
    </button>
  </div>
  <div v-show="active">
    <p v-bind:key="i" v-for="i in dataMain.length" class="block-info">
      {{ dataMain[i - 1] }}
    </p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      active: false,
      dataMain: "",
    };
  },
  methods: {
    btn(i) {
      this.dataMain = "";
      this.dataMain = this.data[i - 1];
      this.active = true;
      this.closeFunc();
    },
  },
  props: ["data", "count", "countForString", "closeFunc"],
};
</script>

<style scoped>
.btnTab {
  position: relative;
  border: 0;
  transition: 0.5s;
  padding: 17px;
  margin-right: 5px;
  width: 80px;
}
.btnTab:hover {
  background: black;
  color: white;
}
.flex {
  position: absolute;
  left: 350px;
  top: 80px;
  justify-content: center;
  margin: 0px 40% 10px;
  display: flex;
}
.block-info {
  user-select: none;
  font-size: 17px;
  background: grey;
  width: 30%;
  padding: 12px;
  margin-bottom: 0px;
  margin-top: 4px;
  margin: 4px 35% 0;
}
</style>