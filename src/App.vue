<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <TabelBase :data="tableData" :columns="columns" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import TabelBase from "./components/TabelBase.vue";

export default {
  name: "app",
  components: {
    HelloWorld,
    TabelBase
  },
  data() {
    return {
      columns: [
        { prop: "date", label: "日期", width: "" },
        { prop: "name", label: "姓名", width: "" },
        { prop: "address", label: "地址", width: "" },
        {
          label: "操作",
          width: "",
          render: (h, params) => {
            return h("div", [
              h(
                "el-button",
                {
                  props: {
                    type: "primary",
                    size: "small"
                  },
                  style: {
                    marginRight: "5px"
                  },
                  on: {
                    click: () => {
                      console.log(params.index);
                    }
                  }
                },
                "View"
              ),
              h(
                "el-button",
                {
                  props: {
                    type: "error",
                    size: "small"
                  },
                  on: {
                    click: () => {
                      console.log(params.index);
                    }
                  }
                },
                "Delete"
              )
            ]);
          }
        }
      ],
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ]
    };
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
