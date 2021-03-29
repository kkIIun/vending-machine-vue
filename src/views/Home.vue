<template>
  <div>
    <h1>Welcome to {{ title }}!</h1>
    <input type="text" v-model="input1" />
    <button type="button" @click="getData">Get</button>
    <button type="button" @click="setData">Set</button>
    <br />
    <select
      name="citiy"
      id="form-control"
      v-model="region"
      @change="changeRegion"
    >
      <option :key="i" :value="d.v" v-for="(d, i) in opions">{{ d.t }}</option>
    </select>

    <table class="table" v-if="tableShow">
      <tr :key="i" v-for="(d, i) in opions">
        <td>{{ d.v }}</td>
        <td>{{ d.t }}</td>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: "개발자의 품격",
      input1: "abc",
      opions: [
        { v: "S", t: "Seoul" },
        { v: "J", t: "Jeju" },
        { v: "B", t: "Busan" },
      ],
      region: "J",
      tableShow: false,
    };
  },
  // 데이터 변경을 캐치
  watch: {
    input1() {
      console.log(this.input1);
    },
  },
  methods: {
    getData() {
      alert(this.input1);
    },
    setData() {
      this.input1 = "12345";
    },
    changeRegion() {
      this.tableShow = true;
    },
  },
  // 특정 데이터를 db에서 갔고오는 시점
  beforeCreate() {
    console.log("bc");
  },
  created() {
    console.log("c");
  },
  // 화면을 로딩하는 시점
  beforeMount() {
    console.log("bm");
  },
  mounted() {
    console.log("m");
  },
  // 값이 업데이트되는 시점
  beforeUpdate() {
    console.log("bU");
  },
  updated() {
    console.log("u");
  },
  // 값이 삭제되는 시점
  beforeDestroy() {
    console.log("bd");
  },
  destroyed() {
    console.log("d");
  },
};
</script>
