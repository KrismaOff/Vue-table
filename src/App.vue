<template>
  <h1>App</h1>
  <button class="btn cr" @click="active = true">Create a table</button>

  <div class="block-input">
    <div v-show="active">
      <InputBlock
        v-bind:key="i"
        v-for="i in count.length"
        :changeData="changeData"
      />

      <button @click="btn" class="btn">add</button>
      <button @click="commit" class="btn">commit</button><br />
    </div>

    <div class="inp-tbl-block">
      <InputTable
        v-show="arrayWithOptionsForProps.length != 0"
        :changeData="changeData"
        :data="arrayWithOptionsForProps"
        :confirm="confirm"
        :commit="commit"
      />
    </div>
    <InputPlace
      :data="arrayWithOptionsConfirm"
      :count="countForTab"
      :countForString="countForString"
      :closeFunc="closeFunc"
    />
  </div>
</template>

<script>
import InputTable from "./components/InputTable.vue";
import InputBlock from "./components/Input.vue";
import InputPlace from "./components/InputPlace.vue";
export default {
  name: "App",
  components: {
    InputTable,
    InputBlock,
    InputPlace,
  },
  data() {
    return {
      active: false, // v-show
      activeForPlace: false,
      count: [0], // count of string
      countForTab: 0,
      countForString: [],
      arrayWithOptions: [],
      arrayWithOptionsForProps: [],
      arrayWithOptionsConfirm: [],
    };
  },
  methods: {
    btn() {
      this.count.push(1);
    },
    changeData(i) {
      this.arrayWithOptions.push(i);
    },
    commit() {
      this.arrayWithOptionsForProps = this.arrayWithOptions;
      this.active = false;
    },
    confirm(data) {
      this.arrayWithOptionsConfirm.push(data);
      this.arrayWithOptionsForProps = []; //v-show
      this.arrayWithOptions = []; //inputTable
      this.countForTab++;
      this.countForString = this.count;
      this.count = [0];
    },
    closeFunc() {
      this.active = false;
    },
  },
};
</script>

<style>
h1 {
  text-align: center;
}
.cr {
  margin-left: 42%;
  margin-bottom: 10px;
}
.btn {
  font-size: 15px;
  width: 16%;
  padding: 16px;
  border-radius: 0;
  border: 0;
  transition: 0.5s;
}
.btn:hover {
  background: black;
  color: white;
}
.block-input {
  text-align: center;
}
.inp-tbl-block {
  display: flex;
  justify-content: center;
}
</style>
