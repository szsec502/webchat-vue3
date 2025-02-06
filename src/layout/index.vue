<script setup>
import { ref } from 'vue';
import { ChatLineRound, List, Fold, Expand } from '@element-plus/icons-vue';

const isCollapse = ref(false);

const toggleSidebar = () => {
  isCollapse.value = !isCollapse.value;
};
</script>

<template>
  <el-container class="app-container">
    <el-aside :width="isCollapse ? '64px' : '240px'" style="border-right: 1px solid #e6e6e6; transition: width 0.3s;">
      <div class="sidebar-header">
        <div class="logo" :class="{ 'collapsed': isCollapse }">  
          AI Chat
        </div>
        <el-icon class="toggle-icon" @click="toggleSidebar">
          <component :is="isCollapse ? Expand : Fold" />
        </el-icon>
      </div>
        <el-menu
          style="height: calc(100% - 60px); background-color: #f9f9f9;"
          class="sidebar-menu"
          :collapse="isCollapse"
        >
          <el-menu-item index="1">
            <el-icon><ChatLineRound /></el-icon>
            <span>新对话</span>
          </el-menu-item>
          <el-menu-item index="2">
            <el-icon><List /></el-icon>
            <span>历史记录</span>
          </el-menu-item>
        </el-menu>
      </el-aside>
      
      <el-main style="padding: 0;">
        <slot></slot>
      </el-main>
  </el-container>
</template>

<style scoped>
.app-container {
  height: 100vh;
  display: flex;
  overflow: hidden;
}

.el-main {
  flex: 1;
  overflow: hidden;
  padding: 0;
}

.sidebar-header {
  height: 60px;
  padding: 0 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #e6e6e6;
  background-color: #ffffff;
}

.logo {
  font-size: 20px;
  font-weight: bold;
  color: #409EFF;
  white-space: nowrap;
  overflow: hidden;
  transition: all 0.3s;
}

.logo.collapsed {
  font-size: 16px;
}

.toggle-icon {
  cursor: pointer;
  font-size: 20px;
  color: #909399;
}

.toggle-icon:hover {
  color: #409EFF;
}

@media (max-width: 768px) {
  .el-aside {
    width: 60px !important;
  }
  
  .logo {
    font-size: 16px;
  }
  
  .logo.collapsed {
    display: none;
  }
}
</style>