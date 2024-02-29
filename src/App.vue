<template>
  <a-layout>
    <a-layout-sider
      breakpoint="lg"
      collapsed-width="0"
      @collapse="onCollapse"
      @breakpoint="onBreakpoint"
    >
      <div class="logo" />
      <p class="text-xs ml-4 text-white">上海正也医药有限公司</p>
      <a-menu v-model:selectedKeys="selectedKeys" theme="dark" mode="inline">
        <a-menu-item key="1">
          <user-outlined />
          <span class="nav-text">nav 1</span>
        </a-menu-item>
        <a-menu-item key="2">
          <video-camera-outlined />
          <span class="nav-text">nav 2</span>
        </a-menu-item>
        <a-menu-item key="3">
          <upload-outlined />
          <span class="nav-text">nav 3</span>
        </a-menu-item>
        <a-menu-item key="4">
          <user-outlined />
          <span class="nav-text">nav 4</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <a-layout>
      <a-layout-header>
        <a-menu v-model:selectedKeys="selectedKeys" theme="dark" mode="horizontal" :items="items">
        </a-menu
      ></a-layout-header>
      <a-layout-content>
        <router-view />
      </a-layout-content>
    </a-layout>
  </a-layout>
</template>
<script setup>
import { ref, h } from 'vue';
import { HomeFilled, CloudFilled, DatabaseFilled } from '@ant-design/icons-vue';
const onCollapse = (collapsed, type) => {
  console.log(collapsed, type);
};
const onBreakpoint = broken => {
  console.log(broken);
};
const selectedKeys = ref(['4']);

const items = ref([
  {
    key: 'home',
    icon: () => h(HomeFilled, { style: 'font-size: 16px;' }),
    label: '首页',
    title: '首页'
  },
  {
    key: 'mainData',
    icon: () => h(CloudFilled),
    label: '主数据',
    title: '主数据'
  },
  {
    key: 'manage',
    icon: () => h(DatabaseFilled),
    label: '辖区管理',
    title: '主数据'
  }
]);
</script>
<style scoped>
.layout {
  height: 100vh;
}
.logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px;
  margin-bottom: 2px;
}

.site-layout-sub-header-background {
  background: #fff;
}

.site-layout-background {
  background: #fff;
}

.site-layout-sub-header-background {
  background: #141414;
}
</style>
