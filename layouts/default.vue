<template>
  <div id="app">
    <el-container>
      <!-- Header  -->
      <el-header>
        <Header />
      </el-header>

      <el-container>
        <!-- Side bar -->
        <el-aside width="250px">
          <side-bar />
        </el-aside>

        <el-container>
          <!-- Content -->
          <el-main>
            <Nuxt />
          </el-main>

          <!-- Footer -->
          <el-footer>
            <Footer />
          </el-footer>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import Header from './Header.vue'
import SideBar from './SideBar.vue'
import Footer from './Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    SideBar,
    Footer
  }
}
</script>

<style>
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.el-header {
  background-color: #3c8dbc;
  color: #ffffff;
  line-height: 60px;
}

.el-footer {
  background: #fff;
  padding: 15px;
  color: #444;
  line-height: 40px;
  text-align: center;
  border-top: 1px solid #d2d6de;
}

.el-main {
  background-color: #ecf0f5;
  padding: 10px !important;
}
</style>
