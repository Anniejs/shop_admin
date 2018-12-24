<template>
  <div class="login">
    <div class="login-box">
  <el-form :model="numberValidateForm" status-icon :rules="rules" ref="numberValidateForm" label-width="100px" class="demo-ruleForm">
    <img src="../assets/images/shop_01.jpg.jpg" alt="">
    <el-form-item
    class='con-ruleForm'
        label="用户名"
        prop="username"
     >
       <el-input placeholder='请输入用户名' v-model="numberValidateForm.username"></el-input>
    </el-form-item>
  <el-form-item label="密码" prop="password">
    <el-input placeholder='请输入密码' v-model="numberValidateForm.password"></el-input>
    </el-form-item>

       <el-form-item>
       <el-button type="primary" @click="submitForm('numberValidateForm')">提交</el-button>
       <el-button @click="resetForm('numberValidateForm')">重置</el-button>
     </el-form-item>
 </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      numberValidateForm: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          {required: true, message: '用户名不能为空', trigger: 'change'},
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'change' }
        ],
        password: [
          { required: true, message: '密码不能为空', trigger: 'change' },
          { min: 6, max: 8, message: '长度在 6 到 8 个字符', trigger: 'change' }
        ]
      }
    }
  },
  methods: {
    submitForm (formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert('submit!')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    resetForm (formName) {
      this.$refs[formName].resetFields()
    }
  }
}
</script>

<style lang='less'>
.login {
  width: 100%;
  height: 100%;
  background-color: #2d434c;
  overflow: hidden;
  .login-box {
    width: 500px;
    height: 300px;
    background-color: #fff;
    margin: 200px auto;
    .demo-ruleForm{
      position: relative;
      padding: 75px 40px 15px;
      border-radius: 20px;
      img{
        width: 140px;
        height: 140px;
        border-radius: 50%;
        position: absolute;
        top:-80px;
        border: 10px solid #fff;
        left: 50%;
        transform: translateX(-50%);

      }
    }
  }
}
</style>
