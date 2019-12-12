<template>
  <div id="app">
    <el-container>
      <el-header style="padding:0 0">
        <Header/>
      </el-header>
      <el-container>
        <el-container>
          <el-aside width="200px">
            <Navigation/>
          </el-aside>
          <el-main>
            <DocumentDetails/>
            <Paging/>
          </el-main>
        </el-container>
      </el-container>
      <el-footer>
        <Footer/>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import DocumentDetails from './components/DocumentDetails'
// import Paging from './components/Paging'
import Navigation from './components/Navigation'
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'app',
  components: {
    // DocumentDetails,
    // Paging,
    Navigation,
    Header,
    Footer
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}
.el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 200px;
  }
  
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  
  body > .el-container {
    margin-bottom: 40px;
  }
  
  .el-container:nth-child(5) .el-aside,
  .el-container:nth-child(6) .el-aside {
    line-height: 260px;
  }
  
  .el-container:nth-child(7) .el-aside {
    line-height: 320px;
  }
</style>
