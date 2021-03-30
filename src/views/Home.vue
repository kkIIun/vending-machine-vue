<template>
  <div class="whole-container">
    <div class="title">자판기</div>
    <div class="vending-machine container">
      <div class="main container">
        <div :key="i" class="drinks" v-for="(d, i) in drinks">
          <img :src="d.img" class="img sticky" height="80%" width="auto" />
          <div class="number sticky">{{i+1}}</div>
          <div class="value sticky">{{d.value}}원</div>
        </div>
      </div>
      <div class="side container"></div>
      <div class="out container"></div>
    </div>
  </div>
  <!-- <div>
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
  </div>-->
</template>
<style>
html {
  font-family: "Noto Sans KR", sans-serif;
  font-size: 14px; /* 1rem = 14px */
}
body {
  margin: 0;
  background-image: url("../images/지하철역.jpg");
  overflow-x: hidden;
  background-size: 100vw 100vh;
  height: 100vh;
}

.title {
  font-weight: bold;
  font-size: 3rem;
}
.whole-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.container {
  border-radius: 11px;
  padding: 25px;
}
.vending-machine {
  background-color: #262626;
  min-width: 666px;
  height: 82%;
  display: flex;
  flex-wrap: wrap;
}
.main,
.side,
.out {
  background-color: white;
}

.main {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  row-gap: 5%;
  column-gap: 8%;
  width: 57%;
  height: 60%;
  margin-right: auto;
}
.side {
  width: 22%;
  height: 60%;
}
.out {
  margin-top: auto;
  width: 92.5%;
  height: 21%;
}
.drinks {
  position: relative;
  border-radius: 15px;
  border: 1px solid black;
  height: 100%;
  width: 100%;
}
.sticky {
  position: absolute;
}
.number {
  top: 5px;
  left: 10px;
}
.img {
  left: 32%;
  top: 0;
}
.value {
  bottom: 5px;
  left: 33%;
}
</style>
<script>
export default {
  data() {
    return {
      drinks: [
        { img: require("../images/데자와.png"), value: "1000" },
        { img: require("../images/펩시.png"), value: "1200" },
        { img: require("../images/핫식스.png"), value: "1100" },
        { img: require("../images/레쓰비.png"), value: "800" },
        { img: require("../images/코코팜.png"), value: "900" },
        { img: require("../images/옥수수수염차.png"), value: "1200" },
        { img: require("../images/파워에이드.png"), value: "1000" },
        { img: require("../images/초코라떼.png"), value: "700" },
        { img: require("../images/아이시스.png"), value: "800" },
        { img: require("../images/밀키스.png"), value: "1000" },
        { img: require("../images/코카콜라.png"), value: "1400" },
        { img: require("../images/게토레이.png"), value: "1000" }
      ]
    };
  },
  // 데이터 변경을 캐치
  watch: {
    input1() {
      console.log(this.input1);
    }
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
    }
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
  }
};
</script>
