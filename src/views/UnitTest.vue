<template>
  <div class="unittest">
    <el-row>
      <h1 style="font-size: 18px" >单元测试</h1>
    </el-row>
    <el-row style="display: flex;">
      <div>
      <el-select
        v-model="selected"
        class="m-2"
        placeholder="选择需要测试的微服务"
        size="large"
      >
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        />
      </el-select>
    </div>

      <el-button type="primary" style="margin-left: 15px;height: 40px;" @click="unitTesting"
        >进行测试</el-button
      >
    </el-row>
  </div>
</template>


<script>
import axios from "axios";
export default {
  name: "UnitTest",
  data() {
    return {
      options: [
        {
          value: "http://localhost:8090/test/unit",
          label: "高校机构微服务",
        },
        {
          value: "http://localhost:8083/test/unit",
          label: "个人中心微服务",
        },
        {
          value: "http://localhost:8081/test/unit",
          label: "登陆注册微服务",
        },
        {
          value: "http://localhost:8093/test/unit",
          label: "动态微服务",
        },
      ],
      selected: "",
      tableData: [],
      fileList: []
    };
  },
  methods: {
    unitTesting() {
      console.log(this.selected);
      axios({
        url: this.selected,
        method: "get",
      })
        .then((res) => {
          console.log(res);
        })
        .catch((errMsg) => {
          console.log(errMsg);
          console.log("预测失败");
        });
    },
  },
};
</script>

<style scoped>
</style>