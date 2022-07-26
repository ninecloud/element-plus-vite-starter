<template>
  <el-menu
    default-active="2"
    class="el-menu-vertical-demo"
    :collapse="isCollapse"
    @open="handleOpen"
    @close="handleClose"
  >
    <el-menu-item index="1">
        <el-icon><Plus /></el-icon>
      <template #title>数据源</template>
    </el-menu-item>

    <el-menu-item index="2">
      <el-icon><Filter /></el-icon>
      <template #title>过滤+字段设置</template>
    </el-menu-item>

    <el-menu-item index="3">
      <el-icon><Coin /></el-icon>
      <template #title>分组汇总</template>
    </el-menu-item>

    <el-menu-item index="4">
      <el-icon><Connection /></el-icon>
      <template #title>左右连接</template>
    </el-menu-item>

    <el-menu-item index="5">
      <el-icon><DCaret /></el-icon>
      <template #title>上下连接</template>
    </el-menu-item>

    <el-menu-item index="6">
      <el-icon><Finished /></el-icon>
      <template #title>结束</template>
    </el-menu-item>
  </el-menu>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import {
  Menu as IconMenu,
  Coin,
  Plus,
  Filter,
  Connection,
  DCaret,
  Finished
} from '@element-plus/icons-vue'

const isCollapse = ref(true)
const handleOpen = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
const handleClose = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
</script>

