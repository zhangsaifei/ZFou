<template>
    <div>
        <el-dialog :visible="dialogFormVisible" :before-close="handleClose">
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="功能名称" prop="projectName" required>
                    <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
                <el-form-item label="提交人" prop="persion">
                    <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>

                <el-form-item label="版本" prop="version" required style="text-align:left">
                    <el-select v-model="ruleForm.region" placeholder="请选择版本号" >
                    <el-option label="DCV5.1.0" value="5.1.0"></el-option>
                    <el-option label="DCV5.2.0" value="5.2.0"></el-option>
                    <el-option label="DCV5.3.0" value="5.3.0"></el-option>
                    <el-option label="DCV5.4.0" value="5.4.0"></el-option>
                    </el-select>
                </el-form-item>

                <el-form-item label="上传代码" prop="uploadCode" required style="text-align:left">
                    <el-upload
                        class="upload-demo"
                        action="https://jsonplaceholder.typicode.com/posts/"
                        :on-change="handleChange"
                        :file-list="CodeFileList">
                        <el-button size="small" type="primary">点击上传</el-button>
                        <!-- <div slot="tip" class="el-upload__tip">只能上传zip/rar文件，且不超过50kb</div> -->
                    </el-upload>
                </el-form-item>
                <el-form-item label="上传DEMO" prop="uploadDemo" style="text-align:left">
                    <el-upload
                        class="upload-demo"
                        action="https://jsonplaceholder.typicode.com/posts/"
                        :on-change="handleChange"
                        :file-list="DemoFileList">
                        <el-button size="small" type="primary">点击上传</el-button>
                        <!-- <div slot="tip" class="el-upload__tip">只能上传zip/rar文件，且不超过50kb</div> -->
                    </el-upload>
                </el-form-item>
                
                <el-form-item label="功能描述" prop="desc">
                    <el-input type="textarea" v-model="ruleForm.desc"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
                    <!-- <el-button @click="resetForm('ruleForm')">重置</el-button> -->
                </el-form-item>
            </el-form>
        </el-dialog>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        ruleForm: {
          name: '',
          projectName: '',
          persion: '',
          varsion: '',
          uploadCode: '',
          uploadDemo: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: '',
          DemoFileList: '',
          CodeFileList: ''
        },
        formLabelWidth: '120px',
        rules: {
          name: [
            { required: true, message: '请输入活动名称', trigger: 'blur' },
            { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
          ],
          region: [
            { required: true, message: '请选择活动区域', trigger: 'change' }
          ],
          date1: [
            { type: 'date', required: true, message: '请选择日期', trigger: 'change' }
          ],
          date2: [
            { type: 'date', required: true, message: '请选择时间', trigger: 'change' }
          ],
          type: [
            { type: 'array', required: true, message: '请至少选择一个活动性质', trigger: 'change' }
          ],
          resource: [
            { required: true, message: '请选择活动资源', trigger: 'change' }
          ],
          desc: [
            { required: true, message: '请填写详细的功能描述', trigger: 'blur' }
          ]
        }
      };
    },
    props: ['dialogFormVisible'],
    methods: {
        handleClose(done) {
            this.$emit('close-browse', false);
            done();
        },
        submitForm(formName) {
            this.$refs[formName].validate((valid) => {
            if (valid) {
                alert('submit!');
            } else {
                console.log('error submit!!');
                return false;
            }
            });
        },
        resetForm(formName) {
            this.$refs[formName].resetFields();
        }
    }
  };
</script>
