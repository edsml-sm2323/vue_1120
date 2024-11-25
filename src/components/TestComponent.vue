<!--<template>-->
<!--  <div class="menu-container">-->
<!--    <el-dropdown-->
<!--      trigger="click"-->
<!--      placement="top-start"-->
<!--      @command="handleCommand"-->
<!--    >-->
<!--      <el-button>-->
<!--        菜单 <el-icon><ArrowDown /></el-icon>-->
<!--      </el-button>-->
<!--      <template #dropdown>-->
<!--        <el-dropdown-menu>-->
<!--          <el-dropdown-item command="1">选项一</el-dropdown-item>-->
<!--          <el-dropdown-item command="2">选项二</el-dropdown-item>-->
<!--          <el-dropdown-item command="3">选项三</el-dropdown-item>-->
<!--        </el-dropdown-menu>-->
<!--      </template>-->
<!--    </el-dropdown>-->
<!--  </div>-->
<!--</template>-->

<!--<script>-->
<!--import { ArrowDown } from "@element-plus/icons-vue";-->

<!--export default {-->
<!--  name: "DropdownMenu",-->
<!--  components: {-->
<!--    ArrowDown,-->
<!--  },-->
<!--  methods: {-->
<!--    handleCommand(command) {-->
<!--      console.log(`选中了选项 ${command}`);-->
<!--    },-->
<!--  },-->
<!--};-->
<!--</script>-->

<!--<style scoped>-->
<!--.menu-container {-->
<!--  margin-top: 100px; /* 防止下拉菜单超出页面 */-->
<!--  display: flex;-->
<!--  justify-content: center;-->
<!--}-->
<!--</style>-->


<template>
  <div class="menu-container">
    <!-- 菜单按钮 -->
    <el-dropdown
      trigger="click"
      placement="top-start"
      popper-class="custom-dropdown-menu"
      @command="handleCommand"
    >
      <el-button size="mini">
        菜单 <el-icon><ArrowDown /></el-icon>
      </el-button>
      <template #dropdown>
        <el-dropdown-menu>
          <el-dropdown-item command="1">选项一</el-dropdown-item>
          <el-dropdown-item command="2">选项二</el-dropdown-item>
          <el-dropdown-item command="3">选项三</el-dropdown-item>
        </el-dropdown-menu>
      </template>
    </el-dropdown>
  </div>
</template>

<script>
import { ArrowDown } from "@element-plus/icons-vue";

export default {
  name: "DropdownMenu",
  components: {
    ArrowDown,
  },
  methods: {
    handleCommand(command) {
      console.log(`选中了选项 ${command}`);
    },
  },
};
</script>

<style scoped>
/* 外层容器 */
.menu-container {
  margin-top: 100px; /* 防止菜单超出页面 */
  display: flex;
  justify-content: center; /* 水平居中 */
  width: 300px; /* 外层 div 的宽度 */
}

/* 自定义下拉菜单宽度 */
.custom-dropdown-menu {
  width: 100% !important; /* 菜单宽度与父容器一致 */
  min-width: unset !important; /* 防止 Element Plus 默认的最小宽度限制 */
}

.custom-dropdown-menu .el-dropdown-menu__item {
  text-align: left; /* 菜单项内容左对齐 */
}

.el-button {
  border-radius: 12px; /* 圆角按钮 */
}
</style>
