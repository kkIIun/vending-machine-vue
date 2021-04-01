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
      <div class="side container">
        <div class="top">
          <div class="drink_number border">{{number}}</div>
          <div class="drink_value border">{{value}}</div>
        </div>
        <div class="numbers">
          <button :key="i" class="number" v-for="i in 9" @click="setData($event)">{{i}}</button>
        </div>
        <div class="button">
          <button type="submit" @click="rank($event)">입력</button>
        </div>
        <div class="rank border">
          <div
            :key="index"
            class="rank_ele"
            v-for="(key,value,index) in ranking"
          >{{index+1}}. {{value}}({{key}})</div>
        </div>
      </div>
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

.container:not(.side) {
  border-radius: 11px;
  padding: 25px;
}

.vending-machine {
  background-color: #262626;
  min-width: 560px;
  height: 82%;
  display: flex;
  flex-wrap: wrap;
}

.main,
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
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 22%;
  height: 67%;
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

.border {
  border: 1px solid black;
}

.numbers {
  margin-bottom: 0.5rem;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  row-gap: 12%;
  column-gap: 15%;
  width: 70%;
  height: 21%;
}

.side .number {
  border: 1px solid black;
  border-radius: 10px;
  width: 100%;
  height: 100%;
}

.top {
  width: 100%;
  height: 7%;
  margin-bottom: 1rem;
}

.drink_number {
  text-align: center;
  background-color: white;
  display: inline-block;
  height: 100%;
  width: 30%;
  margin-right: 6%;
}

.drink_value {
  text-align: center;
  background-color: white;
  display: inline-block;
  height: 100%;
  width: 60%;
}

.rank {
  display: flex;
  flex-direction: column;
  background-color: white;
  width: 100%;
  height: 100%;
  margin-top: 1rem;
  border-radius: 17px;
}
</style>
<script>
export default {
  data() {
    return {
      drinks: [
        {
          img: require("../images/데자와.png"),
          value: "1000",
          num: "1",
          title: "데자와"
        },
        {
          img: require("../images/펩시.png"),
          value: "1200",
          num: "2",
          title: "펩시"
        },
        {
          img: require("../images/핫식스.png"),
          value: "1100",
          num: "3",
          title: "핫식스"
        },
        {
          img: require("../images/레쓰비.png"),
          value: "800",
          num: "4",
          title: "레쓰비"
        },
        {
          img: require("../images/코코팜.png"),
          value: "900",
          num: "5",
          title: "코코팜"
        },
        {
          img: require("../images/옥수수수염차.png"),
          value: "1200",
          num: "6",
          title: "옥수수수염차"
        },
        {
          img: require("../images/파워에이드.png"),
          value: "1000",
          num: "7",
          title: "파워에이드"
        },
        {
          img: require("../images/초코라떼.png"),
          value: "700",
          num: "8",
          title: "초코라떼"
        },
        {
          img: require("../images/아이시스.png"),
          value: "800",
          num: "9",
          title: "아이시스"
        },
        {
          img: require("../images/밀키스.png"),
          value: "1000",
          num: "10",
          title: "밀키스"
        },
        {
          img: require("../images/코카콜라.png"),
          value: "1400",
          num: "11",
          title: "코카콜라"
        },
        {
          img: require("../images/게토레이.png"),
          value: "1000",
          num: "12",
          title: "게토레이"
        }
      ],
      number: "",
      value: "",
      ranking: {}
    };
  },
  // 데이터 변경을 캐치
  watch: {
    input1() {
      console.log(this.input1);
    }
  },
  methods: {
    rank() {
      let title = this.drinks[this.number].title;
      if (title in this.ranking) {
        this.$set(this.ranking, title, this.ranking[title] + 1);
      } else {
        this.$set(this.ranking, title, 1);
      }
    },
    setData(event) {
      if (this.number.length > 1) this.number = "";
      this.number += event.currentTarget.innerText;
      if (this.number * 1 > 12) {
        this.number = "Null";
        this.value = "Null";
      } else {
        this.value = this.drinks[this.number].value + "원";
      }
    },
    changeRegion() {
      this.tableShow = true;
    }
  },
  // 특정 데이터를 db에서 갔고오는 시점
  beforeCreate() {},
  created() {},
  // 화면을 로딩하는 시점
  beforeMount() {},
  mounted() {},
  // 값이 업데이트되는 시점
  beforeUpdate() {},
  updated() {},
  // 값이 삭제되는 시점
  beforeDestroy() {},
  destroyed() {}
};
</script>
