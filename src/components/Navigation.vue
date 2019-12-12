
<template>
  <el-tabs :tab-position="tabPosition" style="min-height: 700px;">
    <el-tab-pane label="DCV">
      <DocumentDetails/>
    </el-tab-pane>
    <el-tab-pane label="Proxima">
      <DocumentDetails/>
    </el-tab-pane>
    <el-tab-pane label="DMV">
      <DocumentDetails/>
    </el-tab-pane>
    <el-tab-pane label="TEST">
      TEST
    </el-tab-pane>
  </el-tabs>
</template>
<script>

  import DocumentDetails from './DocumentDetails'
  export default {
    data() {
      return {
        tabPosition: 'left'
      };
    },
    components: {
      DocumentDetails
    }
  };
</script>