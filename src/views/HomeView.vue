<script setup>
import {
  Search,
  Document,
  Menu as IconMenu,
  Location,
  Setting,
  RefreshLeft,
  Plus,
} from "@element-plus/icons-vue";
import { reactive, ref } from "vue";

//当前页
const pageNum = ref(2);
//页数
const pageSize = ref(10);
const name = ref("");
const state = reactive({
  tableData: [
    { name: "admin", address: "合肥市庐阳区", phone: "123431232" },
    { name: "admin", address: "合肥市庐阳区", phone: "123431232" },
    { name: "admin", address: "合肥市庐阳区", phone: "123431232" },
  ],
});

//复选框
const multipleSelection = ref([])
const handleSelectionChange = (val) => {
  multipleSelection.value = valx`x`
}
</script>

<template>
  <div>
    <div
      style="
        height: 60px;
        line-height: 60px;
        border-bottom: 1px solid #ccc;
        background-color: aliceblue;
      "
    >
      <div style="display: flex">
        <div
          style="
            width: 200px;
            color: dodgerblue;
            font-weight: bold;
            text-align: center;
            font-size: 20px;
          "
        >
          后台管理
        </div>

        <div style="flex: 1; display: flex">
          <div style="flex: 1"></div>
          <div style="width: 200px; text-align: right; padding-right: 20px">
            头像
          </div>
        </div>
      </div>
    </div>
    <div style="display: flex">
      <div
        style="
          width: 200px;
          min-height: calc(100vh-60px);
          border-right: 1px solid #ccc;
        "
      >
        <!-- 加入router 会使得下面index内容都变成路由跳转地址
            default-active="/" 这个""里面的和下面index对应都会变成高亮显示-->
        <el-menu router default-active="/" class="el-menu-vertical-demo">
          <el-sub-menu index="1">
            <template #title>
              <el-icon><location /></el-icon>
              <span>Navigator One</span>
            </template>
            <el-menu-item index="/">item one</el-menu-item>
          </el-sub-menu>
          <el-menu-item index="2">
            <el-icon><icon-menu /></el-icon>
            <span>Navigator Two</span>
          </el-menu-item>
          <el-menu-item index="3" disabled>
            <el-icon><document /></el-icon>
            <span>Navigator Three</span>
          </el-menu-item>
          <el-menu-item index="4">
            <el-icon><setting /></el-icon>
            <span>Navigator Four</span>
          </el-menu-item>
        </el-menu>
      </div>
      <!--flex:1 左边是宽200px 剩余的都属于右边-->
      <div style="flex: 1; padding: 10px">
        <div>
          <el-input
            v-model="name"
            placeholder="请输入名称"
            style="width: 300px"
          />
          <el-input
            v-model="name"
            placeholder="请输入名称"
            style="width: 300px; margin-left: 5px"
          />
          <el-button type="primary" style="margin-left: 5px">
            <el-icon style="vertical-align: middle">
              <Search />
            </el-icon>
            <span style="vertical-align: middle">搜索</span>
          </el-button>

          <el-button type="warning" style="margin-left: 5px">
            <el-icon style="vertical-align: middle">
              <RefreshLeft />
            </el-icon>
            <span style="vertical-align: middle">重置</span>
          </el-button>

          <el-button type="success" style="margin-left: 5px">
            <el-icon style="vertical-align: middle">
              <Plus />
            </el-icon>
            <span style="vertical-align: middle">新增</span>
          </el-button>
        </div>

        <div style="margin: 10px 0">
          <!-- stripe border 有边框的效果 -->
          <el-table :data="state.tableData" stripe border @selection-change="handleSelectionChange">
            <el-table-column type="selection" width="55" />
            <el-table-column prop="name" label="名称"></el-table-column>
            <el-table-column prop="address" label="地址"></el-table-column>
            <el-table-column prop="phone" label="联系方式"></el-table-column>
            <el-table-column label="操作">
              <el-button type="primary">编辑</el-button>
              <el-button type="danger" style="margin-left: 5px">删除</el-button>
            </el-table-column>
          </el-table>
        </div>

        <div style="margin: 10 0">
          <el-pagination
            v-model:current-page="pageNum"
            v-model:page-size="pageSize"
            small
            background
            layout="total, sizes, prev, pager, next, jumper"
            :total="50"
          />
        </div>
      </div>
    </div>
  </div>
</template>
