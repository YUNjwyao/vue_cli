<template>
  <div class="employee">
    <!-- 面包屑导航 -->
    <el-breadcrumb separator="/">
      <el-breadcrumb-item>当前位置：公告管理</el-breadcrumb-item>
      <el-breadcrumb-item><a href="/">公告查询</a></el-breadcrumb-item>
    </el-breadcrumb>
    <!-- 查询输入框 -->
    <el-card>
      <el-row>
        职位：
        <el-select v-model="value" placeholder="请选择职位">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          >
          </el-option>
        </el-select>
        姓名：
        <el-input v-model="input"></el-input>
        身份证号码：
        <el-input v-model="input"></el-input>
      </el-row>
      <el-row>
        性别：
        <el-select v-model="value" placeholder="请选择性别">
          <el-option
            v-for="item in optionsSex"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          >
          </el-option>
        </el-select>
        手机：
        <el-input v-model="input"></el-input>
        所属部门：
        <el-select v-model="value" placeholder="--部门选择--">
          <el-option
            v-for="item in optionsDoor"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          >
          </el-option>
        </el-select>
        <el-button>搜索</el-button>
        <el-button>删除</el-button>
      </el-row>
    </el-card>
    <!-- Table表格 -->
    <el-card>
      <el-table
        ref="multipleTable"
        :data="tableData"
        tooltip-effect="dark"
        style="width: 100%"
        @selection-change="handleSelectionChange"
      >
        <el-table-column type="selection" width="55"> </el-table-column>
        <el-table-column prop="name" label="姓名" width="120">
          <template slot-scope="scope">{{ scope.row.name }}</template>
        </el-table-column>
        <el-table-column prop="sex" label="性别" width="120"> </el-table-column>
        <el-table-column prop="phone" label="手机号码" show-overflow-tooltip>
        </el-table-column>
        <el-table-column prop="sex" label="性别" width="120"> </el-table-column>
        <el-table-column prop="email" label="邮箱" width="120">
        </el-table-column>
        <el-table-column prop="job" label="职位" width="120"> </el-table-column>
        <el-table-column prop="education" label="学历" width="120">
        </el-table-column>
        <el-table-column prop="IdNumber" label="身份证号码" width="120">
        </el-table-column>
        <el-table-column prop="door" label="部门" width="120">
        </el-table-column>
        <el-table-column prop="address" label="联系地址" width="120">
        </el-table-column>
        <el-table-column prop="date" label="建档日期" width="120">
        </el-table-column>
        <el-table-column label="操作" width="120"> </el-table-column>
      </el-table>
      <!-- 分页 -->
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="currentPage4"
        :page-sizes="[100, 200, 300, 400]"
        :page-size="100"
        layout="total, sizes, prev, pager, next, jumper"
        :total="400"
      >
      </el-pagination>
    </el-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: [
        {
          value: "选项1",
          label: "经理",
        },
        {
          value: "选项2",
          label: "职员",
        },
      ],
      optionsSex: [
        {
          value: "选项1",
          label: "男",
        },
        {
          value: "选项2",
          label: "女",
        },
      ],
      optionsDoor: [
        {
          value: "选项1",
          label: "技术部",
        },
        {
          value: "选项2",
          label: "运营部",
        },
      ],
      tableData: [
        {
          name: "王小虎",
          sex: "男",
          phone: "1522369825",
          email: "1173131490@qq.com",
          job: "经理",
          education: "本科",
          IdNumber: "500213213123",
          door: "技术部",
          address: "上海市普陀区金沙江路 1518 弄",
          date: "2016-12-03",
        },
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
      ],
      multipleSelection: [],
    };
  },
  methods: {
    toggleSelection(rows) {
      if (rows) {
        rows.forEach((row) => {
          this.$refs.multipleTable.toggleRowSelection(row);
        });
      } else {
        this.$refs.multipleTable.clearSelection();
      }
    },
    handleSelectionChange(val) {
      this.multipleSelection = val;
    },
  },
};
</script>

<style lang="less" scoped>
.el-card {
  margin-top: 20px;
}
.el-input {
  width: 250px;
}
.el-row {
  margin-top: 10px;
}
.el-button {
  margin-left: 10px;
}
</style>
