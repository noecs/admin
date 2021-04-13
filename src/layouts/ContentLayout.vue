<template>
  <a-layout>
    <!-- 侧栏 -->
    <a-layout-sider v-model:collapsed="collapsed" collapsible :trigger="null">
      <div class="logo"/>
      <a-menu theme="dark" v-model:selectedKeys="selectedKeys" mode="inline">
        <a-menu-item key="1">
          <pie-chart-outlined/>
          <span>Option 1</span>
        </a-menu-item>
        <a-menu-item key="2">
          <desktop-outlined/>
          <span>Option 2</span>
        </a-menu-item>
        <a-sub-menu key="sub1">
          <template #title>
            <span>
              <user-outlined/>
              <span>User</span>
            </span>
          </template>
          <a-menu-item key="3">Tom</a-menu-item>
          <a-menu-item key="4">Bill</a-menu-item>
          <a-menu-item key="5">Alex</a-menu-item>
        </a-sub-menu>
        <a-sub-menu key="sub2">
          <template #title>
            <span>
              <team-outlined/>
              <span>Team</span>
            </span>
          </template>
          <a-menu-item key="6">Team 1</a-menu-item>
          <a-menu-item key="8">Team 2</a-menu-item>
        </a-sub-menu>
        <a-menu-item key="9">
          <file-outlined/>
          <span>File</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <!-- 侧栏end -->
    <a-layout>
      <!-- 顶部 -->
      <a-layout-header>
        <menu-unfold-outlined
            v-if="collapsed"
            class="trigger"
            @click="() => (collapsed = !collapsed)"
        />
        <menu-fold-outlined v-else class="trigger" @click="() => (collapsed = !collapsed)" />
      </a-layout-header>
      <!-- 顶部 end -->

      <!-- 主内容区 -->
      <router-view />
      <!-- 主内容区 end -->

      <!-- 页脚 -->
      <a-layout-footer style="text-align: center">
        Ant Design ©2018 Created by Ant UED
      </a-layout-footer>
      <!-- 页脚 end -->
    </a-layout>
  </a-layout>
</template>

<script>
import {ref} from "vue";
// header icon
import {
  MenuFoldOutlined,
  MenuUnfoldOutlined,
} from '@ant-design/icons-vue';


export default {
  name: "ContentLayout",
  components: {
    MenuFoldOutlined,
    MenuUnfoldOutlined,
  },
  data() {
    return {
      collapsed: ref(false),
      selectedKeys: ref(['1']),
    }
  }
}
</script>

<style scoped>
/* body */
.ant-layout{
  height: 100vh;
}
.site-layout .site-layout-background {
  background: #fff;
}

/* header */
.ant-layout-header .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}
.ant-layout-header .trigger:hover {
  color: #1890ff;
}
.ant-layout-header{
  background: #fff!important;
  padding: 0!important;
}

/* sidebar */
.ant-layout-sider{
  flex: 0 0 220px!important;max-width: 240px!important;min-width: 240px!important;width: 240px!important;
}
.ant-layout-sider-collapsed{
  flex: 0 0 80px!important; max-width: 80px!important; min-width: 80px!important; width: 80px!important;
}
.ant-layout-sider .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.3);
  margin: 16px;
}
</style>