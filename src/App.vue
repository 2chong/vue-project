<script setup>
import { RouterLink, RouterView, useRoute } from 'vue-router'
import {
  Document,
  Menu as IconMenu,
  Setting,
} from '@element-plus/icons-vue'

const route = useRoute()

const handleOpen = (key, keyPath) => {
  console.log(key, keyPath)
}
const handleClose = (key, keyPath) => {
  console.log(key, keyPath)
}
</script>

<template>
  <div class="container">
    <el-row class="nav">
      <el-col :span="24">
        <el-menu
          :default-active="route.path"
          class="el-menu-vertical-demo"
          router
          @open="handleOpen"
          @close="handleClose"
        >
          <el-menu-item index="/">
            <el-icon><icon-menu /></el-icon>
            <RouterLink to="/"><span>Home</span></RouterLink>
          </el-menu-item>
          <el-menu-item index="/about">
            <el-icon><document /></el-icon>
            <RouterLink to="/about"><span>About</span></RouterLink>
          </el-menu-item>
          <el-menu-item index="/test">
            <el-icon><setting /></el-icon>
            <RouterLink to="/test"><span>Test</span></RouterLink>
          </el-menu-item>
        </el-menu>
      </el-col>
    </el-row>

    <div class="content">
      <RouterView />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  width: 100vw;
  height: 100vh;
}

.nav {
  width: 100px;
  display: flex;
}

.content {
  flex: 1;
}
</style>