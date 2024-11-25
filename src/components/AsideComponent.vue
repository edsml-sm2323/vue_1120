<template>
  <div class="aside-content">
  <div class="bottom-div">

    <!-- 历史聊天记录 -->
    <el-scrollbar style="max-height: 400px;">
      <el-menu default-active="2" class="el-menu-vertical-demo">
        <!-- 历史聊天记录子菜单 -->
        <el-sub-menu index="1">
          <template #title>
            <el-icon><Document /></el-icon>
            <span>历史聊天记录</span>
          </template>
          <!-- 使用 v-for 循环生成 20 条聊天记录 -->

          <el-menu-item
            v-for="item in 20"
            :key="item"
            class="scrollbar-demo-item"
          >
            聊天记录 {{ item }}
          </el-menu-item>
        </el-sub-menu>
      </el-menu>
        </el-scrollbar>

    <!-- 参数调整 -->
    <el-scrollbar style="max-height: 400px;">
      <el-menu default-active="2" class="el-menu-vertical-demo">
        <el-sub-menu index="2">
          <template #title>
            <el-icon><Filter /></el-icon>
            <span>参数调整</span>
          </template>
          <!-- 参数输入框 -->
          <el-menu-item index="2-1" class="input-menu-item">
            <p class="input-text">para_1</p>
            <el-input
                v-model="params.para_1"
                placeholder=" "
                class="custom-input"
              />
          </el-menu-item>
          <el-menu-item index="2-2" class="input-menu-item">
            <p class="input-text">para_2</p>
            <el-input
                v-model="params.para_2"
                placeholder=" "
                class="custom-input"
              />
          </el-menu-item>
          <el-menu-item index="2-3" class="input-menu-item">
            <p class="input-text">para_3</p>
            <el-input
                v-model="params.para_3"
                placeholder=" "
                class="custom-input"
              />
          </el-menu-item>
        </el-sub-menu>
      </el-menu>
    </el-scrollbar>

      </div>
    </div>
</template>

<script>
import { Document, Filter } from "@element-plus/icons-vue";

export default {
  name: "AsideComponent",
  components: {
    Document,
    Filter,
  },
  data() {
    return {
      params: {
        para_1: "",
        para_2: "",
        para_3: "",
      },
    };
  },
};
</script>

<style scoped>
/* 样式可以根据需求调整 */
.bottom-div {
  flex: 1; /* 占据剩余80%空间 */
  /*background-color: #e0e0e0; !* 可选：设置背景颜色 *!*/
  padding: 0;
}
.scrollbar-demo-item {
  padding: 10px;
}
.input-menu-item {
  display: flex;
  align-items: center;
  padding: 10px;
}
.input-text {
  margin-right: 10px;
  font-size: 14px;
  color: #333;
}
.custom-input {
  flex: 1;
}
.aside-content {
  display: flex;
  flex-direction: column;
  height: 100%; /* 占满父容器的高度 */
  width: 100%; /* 占满父容器的宽度 */
  margin: 0; /* 移除外边距 */
  padding: 0; /* 移除内边距 */
  box-sizing: border-box; /* 确保宽高包含内边距和边框 */
}

.el-menu-vertical-demo {
  padding: 0; /* 移除 el-menu 的默认内边距 */
  width: 100%;
  margin: 0;

}

.el-menu-item {
  padding: 0 10px; /* 根据需要调整 */
}
</style>