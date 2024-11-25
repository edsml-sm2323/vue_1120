<template>
<div class="canvas">
<div class="mode-select">
  <div class="mode-select2">
  <el-dropdown
      trigger="click"
      placement="top-start"
      popper-class="custom-dropdown-menu"
      @command="handleCommand"
    >
      <el-button size="mini">
        模式 <el-icon><ArrowUp /></el-icon>
      </el-button>
      <template #dropdown>
        <el-dropdown-menu>
          <el-dropdown-item command="1">普通模式</el-dropdown-item>
          <el-dropdown-item command="2">CoT模式</el-dropdown-item>
        </el-dropdown-menu>
      </template>
    </el-dropdown>

  <el-dropdown
      trigger="click"
      placement="top-start"
      popper-class="custom-dropdown-menu"
      @command="handleCommand"
    >
      <el-button size="mini">
        模型 <el-icon><ArrowUp /></el-icon>
      </el-button>
      <template #dropdown>
        <el-dropdown-menu>
          <el-dropdown-item command="1">模型1</el-dropdown-item>
          <el-dropdown-item command="2">模型2</el-dropdown-item>
        </el-dropdown-menu>
      </template>
    </el-dropdown>
    </div>
  <div class="input-box">

        <div class="icon-group">
          <el-button class="icon-button" circle>
            <el-icon><UploadFilled /></el-icon>
          </el-button>
        </div>
    <div class="send_message">
          <el-button @click="sendMessage" class="send-button" circle>
          <el-icon><Promotion /></el-icon>
        </el-button>
    </div>
  </div>

</div>

</div>
</template>

<script>
import {UploadFilled ,Promotion,ArrowUp} from '@element-plus/icons-vue'
export default {
  name: "CanvasComponent",
  components:{
    UploadFilled,
    Promotion,
    ArrowUp,
  },
  methods: {
    handleCommand(command) {
      console.log(`选中了选项 ${command}`);
    },
  },
}
</script>

<style scoped>
/* 网格背景样式 */
.canvas {
  position: relative; /* 确保子元素绝对定位相对于父容器 */
  width: 100%; /* 宽度占满父容器 */
  height: 100%; /* 高度占满父容器 */
  background-image: linear-gradient(to right, #ddd 1px, transparent 1px),
    linear-gradient(to bottom, #ddd 1px, transparent 1px);
  background-size: 20px 20px; /* 网格大小 */
  background-color: white; /* 网格背景颜色 */
  border: 1px solid #ccc; /* 边框样式 */
  margin: 3px;
  margin-right: 2px;
  border-radius: 12px;
}

/*.input-box {*/
/*  position: absolute; !* 绝对定位 *!*/
/*  bottom: 10px; !* 距离底部 10px *!*/
/*  left: 50%; !* 水平居中 *!*/
/*  transform: translateX(-50%); !* 将盒子中心对齐 *!*/
/*  width: 80%; !* 宽度占父容器的 80% *!*/
/*  display: flex;*/
/*  align-items: center;*/
/*  justify-content: space-between; !* 将子元素分布在两侧 *!*/
/*  background-color: #f5f5f5; !* 浅灰色背景 *!*/
/*  padding: 10px;*/
/*  border-radius: 20px;*/
/*  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); !* 添加阴影效果 *!*/
/*}*/

.icon-button {
  background-color: transparent;
  color: black;
  border: none;
}

.icon-button:hover {
  background-color: #e0e0e0;
}

.send-button{
  background-color: transparent;
  color: black;
  border: none;
}

.send-button:hover {
  background-color: #ccc;
}

.custom-dropdown-menu .el-dropdown-menu__item {
  text-align: left; /* 菜单项内容左对齐 */
}
.mode-select {
  position: absolute;
  bottom: 0; /* 对齐到父容器底部 */
  left: 50%; /* 水平居中 */
  transform: translateX(-50%); /* 水平居中调整 */
  display: flex;
  flex-direction: column; /* 改为垂直布局 */
  align-items: center; /* 垂直居中 */
  gap: 10px; /* 上下间距 */
  width: 80%; /* 整体宽度 */
  margin-bottom: 10px;
}

.input-box {
  width: 100%; /* 占满 mode-select 容器宽度 */
  display: flex;
  align-items: center;
  justify-content: space-between; /* 将按钮分布在两侧 */
  background-color: #f5f5f5; /* 浅灰色背景 */
  padding: 10px;
  border-radius: 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* 添加阴影效果 */
}

.mode-select2 {
  width: 100%; /* 占满外层 div 的宽度 */
  display: flex; /* 使用 flex 布局 */
  flex-direction: row; /* 水平排列内部元素 */
  align-items: center; /* 垂直居中 */
  justify-content: flex-start; /* 元素靠左对齐 */
  gap: 5px; /* 元素之间的间距 */
}
</style>