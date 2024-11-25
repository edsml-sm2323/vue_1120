<template>
  <div class="common-layout">
    <el-container class="layout-container">
      <!-- 左侧 Aside 区域 -->
      <el-aside
        v-show="!isCollapsed"
        class="layout-aside"
        :style="{ width: isCollapsed ? '0' : '200px' }"
      >
<!--        <div class="aside-content">Aside Content</div>-->
        <AsideComponent />
      </el-aside>

      <!-- 右侧主要内容 -->
      <el-container class="layout-main">
        <!-- Header 区域 -->
        <el-header class="layout-header">
          <!-- 滑块控制折叠 -->
          <el-switch
            v-model="isCollapsed"
            class="header-switch"

          />
        </el-header>

        <!-- Main 内容 -->
        <el-main class="layout-main-content">
        <!--左侧区域-->
          <div class = "split-pane">
          <div class="left-pane" :style="{ width: leftWidth + 'px' }">
            <CanvasComponent/>
          </div>
            <!-- 可拖拽的分隔线 -->
         <div class="drag-resizer" @mousedown="startDragging"></div>


        <div class="right-pane" :style="{ width: `calc(100% - ${leftWidth}px)` }">
              <div class="right-top">
                <RighttopComponent/>
              </div>
              <div class="drag-resizer2"></div>
              <div class="right-bottom">
                <RightdownComponent/>
              </div>
            </div>
            </div>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import { ref } from "vue";
import AsideComponent from "./components/AsideComponent.vue";
import CanvasComponent from "./components/CanvasComponent";
import RighttopComponent from "./components/RighttopComponent";
import RightdownComponent from "./components/RightdownComponent";

export default {
  name: "CommonLayout",
  components: {
    AsideComponent,
    CanvasComponent,
    RighttopComponent,
    RightdownComponent,
  },
  data() {
    return {
      isDragging: false, // 是否正在拖拽
      leftWidth: 300, // 左侧区域的初始宽度
    };
  },

methods: {
    startDragging() {
      this.isDragging = true;
      document.addEventListener("mousemove", this.onDrag);
      document.addEventListener("mouseup", this.stopDragging);
    },
    onDrag(event) {
      if (this.isDragging) {
        const containerRect = this.$el.querySelector(".split-pane").getBoundingClientRect();
        // 计算新的左侧宽度，限制最小和最大值
        this.leftWidth = Math.max(
          50, // 最小宽度
          Math.min(event.clientX - containerRect.left, containerRect.width - 50) // 最大宽度
        );
      }
    },
    stopDragging() {
      this.isDragging = false;
      document.removeEventListener("mousemove", this.onDrag);
      document.removeEventListener("mouseup", this.stopDragging);
    },
  },
  setup() {
    // 控制 Aside 是否折叠
    const isCollapsed = ref(false);
    return {

      isCollapsed,
    };
  },
};
</script>




<style scoped>
/* 页面整体布局 */
.common-layout {
  height: 100vh; /* 占满视口高度 */
}

/* Flex 布局容器 */
.layout-container {
  display: flex;
  height: 100%; /* 高度占满父容器 */
  padding: 0;
  margin:0;
}

/* 左侧 Aside 样式 */
.layout-aside {
  background-color: #f0f2f5;
  transition: width 0.3s ease, opacity 0.3s ease;
  overflow: hidden;
  width: 200px; /* 默认宽度 */
  padding:6px;
}

.layout-aside[style*="width: 0"] {
  display: none; /* 折叠时隐藏 */
}



/* 右侧主要内容 */
.layout-main {
  display: flex;
  flex-direction: column; /* 垂直排列 Header 和 Main */
  flex: 1; /* 填满 Aside 以外的空间 */
}

/* Header 样式 */
.layout-header {
  background-color: #b3c0d1;
  color: white;
  text-align: left;
  line-height: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  padding: 0 20px;
  position: relative;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* 增加阴影 */
}

/* Header 的滑块样式 */
.header-switch {
  margin-right: auto;
}

/* Main 内容样式 */
.layout-main-content {
  flex: 1;
  background-color: #e9eef3;
  padding: 6px;
  text-align: center;
}

.split-pane {
  display: flex; /* 横向排列子元素 */
  width: 100%; /* 占满父容器宽度 */
  height: 100%; /* 占满父容器高度 */
}

.left-pane{
  background-color: #e9eef3;
  text-align: center; /* 居中对齐文本 */
  display: flex; /* 让子内容居中对齐 */
  align-items: center; /* 垂直居中 */
  justify-content: center; /* 水平居中 */
}

.drag-resizer {
  width: 3px;
  background-color: whitesmoke; /* 分隔线颜色 */
  cursor: col-resize; /* 鼠标样式 */
  flex-shrink: 0; /* 防止分隔线收缩 */
}



.right-pane {
  display: flex;
  flex-direction: column; /* 改为上下排列 */
  height: 100%; /* 确保占满父容器的高度 */
  /*background-color: #e9eef3;*/
  text-align: center; /* 居中对齐文本 */
  align-items: center; /* 垂直居中 */
  justify-content: center; /* 水平居中 */

}

.right-top,
.right-bottom {
  flex: 1; /* 两部分均分父容器高度 */
  width: 100%; /* 确保占满父容器宽度 */
  text-align: center; /* 文本居中 */
  display: flex; /* 子内容居中对齐 */
  align-items: center; /* 垂直居中 */
  justify-content: center; /* 水平居中 */
  padding: 0;
  margin: 3px;
}


</style>
