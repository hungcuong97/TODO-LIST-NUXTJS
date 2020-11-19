<template>
  <div id="side-bar">
    <el-menu
      default-active="1"
      class="el-menu-vertical-demo"
      background-color="#222D32"
      text-color="#ffffff"
      active-text-color="#ffd04b"
    >
      <el-menu-item
        v-for="item in sideBarData"
        :key="item.index"
        :index="item.index"
        @click="handleMenu(item.path)"
      >
        <i :class="item.icon" />
        <span>{{ item.name }}</span>
      </el-menu-item>
    </el-menu>
  </div>
</template>

<script>
export default {
  name: 'SideBar',
  data () {
    return {
      sideBarData: [
        {
          index: '1',
          name: 'Trang chủ',
          icon: 'el-icon-menu',
          path: '/'
        },
        {
          index: '2',
          name: 'Quản lý công việc',
          icon: 'el-icon-menu',
          path: '/task'
        },
        {
          index: '3',
          name: 'Liên hệ',
          icon: 'el-icon-phone',
          path: '/contact'
        },
        {
          index: '4',
          name: 'Hỗ trợ ?',
          icon: 'el-icon-setting',
          path: '/help'
        }
      ]
    }
  },
  methods: {
    handleMenu (path) {
      this.$router.push(path)
    }
  }
}
</script>

<style>
.el-menu {
  height: 100vh;
}
</style>
