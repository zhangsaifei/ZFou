<template>
<div>
    <el-dialog
        title="收货地址"
        width="70%"
        :before-close="handleClose"
        :visible="browseVisible">
        <el-table :data="gridData">
            <el-table-column property="date" label="日期" width="150"></el-table-column>
            <el-table-column property="name" label="姓名" width="200"></el-table-column>
            <el-table-column property="address" label="地址"></el-table-column>
        </el-table>
    </el-dialog>
    </div>
</template>

<script>
export default {
    data(){
        return {
            gridData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
            }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
            }]
        }
    },
    props: ['browseVisible'],
    methods: {
        handleClose(done) {
            // this.dialogTableVisible = false;
            console.log('start to parent');
            // this.browseVisible = false
            this.$emit('close-browse', false);
            done();
        }
    }
} 
</script>