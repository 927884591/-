<template>
  <div>
    <div id="title">
      <h1>亲戚计算器</h1>
    </div>
    <div class="main">
      <div>
        <input v-model="show" type="text" name="" id="" class="show" />
      </div>
      <div>
        <input v-model="result" type="text" class="result" />
      </div>
    </div>
    <table>
      <tr>
        <td @click="h">夫</td>
        <td @click="w">妻</td>
        <td @click="del">删除</td>
        <td @click="clear">清空</td>
      </tr>
      <tr>
        <td @click="f">父</td>
        <td @click="m">母</td>
        <td @click="b">兄</td>
        <td @click="bd">弟</td>
      </tr>
      <tr>
        <td @click="s">姐</td>
        <td @click="ys">妹</td>
        <td @click="son">子</td>
        <td @click="daughter">女</td>
      </tr>
    </table>
  </div>
</template>

<script>
import relationship from "relationship.js";
export default {
  name: "App",
  components: {},
  data() {
    return {
      result: "",
      show: "我",
      default: "的",
      option: {
        text: "",
        sex: 1,
      },
    };
  },
  methods: {
    clear() {
      this.option.text = "我";
      this.show = this.option.text;
      this.result = "我";
    },
    del() {
      let length = this.option.text.length;
      this.show = this.option.text = this.option.text.slice(0, length - 3);
      this.result = relationship(this.option);
    },
    getRelation(rel) {
      if (this.option.text) {
        this.option.text += this.default + rel;
      } else {
        this.option.text = "我" + this.default + rel;
      }
      this.show = this.option.text;
      this.result = relationship(this.option);
    },
    h() {
      this.getRelation("丈夫");
    }, //丈夫
    w() {
      this.getRelation("妻子");
    },
    f() {
      this.getRelation("父亲");
    },
    m() {
      this.getRelation("母亲");
    },
    b() {
      this.getRelation("兄弟");
    },
    bd() {
      this.getRelation("弟弟");
    },
    s() {
      this.getRelation("姐姐");
    },
    ys() {
      this.getRelation("妹妹");
    },
    son() {
      this.getRelation("儿子");
    },
    daughter() {
      this.getRelation("女儿");
    },
  },
  mounted() {
    console.log(relationship(this.option)["0"]);
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#title {
  position: absolute;
  top: 0;
  width: 100%;
}
.main {
  position: relative;
  top: 380px;
}
div .show,
div .result {
  width: 100%;
  height: 24px;
  border: none;
  text-align: right;
  font-size: 24px;
  font-weight: 700;
}
div .result {
  margin-top: 24px;
}
table {
  position: absolute;
  bottom: 0;
  width: 100%;
}
tr {
  display: flex;
  width: 100%;
}
td {
  font-size: 24px;
  height: 100px;
  line-height: 100px;
  flex: 1;
  background-color: #fff;
  border: solid 1px #ddd;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
