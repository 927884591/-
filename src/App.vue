<template>
  <div>
    <input v-model="show" type="text" name="" id="" />
    <input v-model="result" type="text" />
    <table>
      <tr>
        <td @click="h">夫</td>
        <td @click="w">妻</td>
        <td>删除</td>
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
      show: "",
      default: "的",
      option: {
        text: "",
        sex: 1,
      },
    };
  },
  methods: {
    clear() {
      this.option.text = "";
      this.show = this.option.text;
      this.result = "我";
    },
    getRelation(rel) {
      if (this.option.text) {
        this.option.text += this.default + rel;
      } else {
        this.option.text = "我" + this.default + rel;
      }
      this.show = this.option.text;
      // "我" + this.default + relationship(this.option)[0]
      this.result = relationship(this.option);
    },
    h() {
      // if (this.option.text) {
      //   this.option.text += this.default + "丈夫";
      // } else {
      //   this.option.text = "我" + this.default + "丈夫";
      // }
      // this.show = this.option.text;
      // // "我" + this.default + relationship(this.option)[0]
      // this.result = relationship(this.option);
      // console.log(this.result);
      this.getRelation("丈夫");
    }, //丈夫
    w() {
      // if (this.option.text) {
      //   this.option.text += this.default + "妻子";
      // } else {
      //   this.option.text = "我" + this.default + "妻子";
      // }
      // this.show = this.option.text;
      // // "我" + this.default + relationship(this.option)[0]
      // this.result = relationship(this.option);
      this.getRelation("妻子");
    },
    f() {
      // if (this.option.text) {
      //   this.option.text += this.default + "妻子";
      // } else {
      //   this.option.text = "我" + this.default + "妻子";
      // }
      // this.show = this.option.text;
      // // "我" + this.default + relationship(this.option)[0]
      // this.result = relationship(this.option);
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
