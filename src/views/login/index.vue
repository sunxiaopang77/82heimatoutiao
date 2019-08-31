<template>
  <div class="login">
    <el-card class="login-card">
      <div class="logo">
        <img src="../../assets/img/logo_index.png" alt />
      </div>
      <!-- 表单组件 -->
      <el-form ref='loginForm' :model="loginForm" :rules="loginRules">
        <!-- 表单项 -->
        <el-form-item prop="mobile">
          <!-- 放置组件内容 -->
          <!-- 绑定手机号 -->
          <el-input v-model="loginForm.mobile" placeholder="请输入手机号"></el-input>
        </el-form-item>
        <el-form-item prop="code">
            <!-- 绑定验证码 -->
          <el-input v-model="loginForm.code" style="width:280px" placeholder="请输入验证码"></el-input>
          <el-button style="float:right">发送验证码</el-button>
        </el-form-item>
        <el-form-item prop="check">
            <!-- 绑定勾选协议 -->
          <el-checkbox v-model="loginForm.check">我已阅读并同意用户协议和隐私条款</el-checkbox>
        </el-form-item>
        <el-form-item>
          <el-button @click="login" type="primary" style="width:100%">登录</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    let validator = function (rule, value, callBack) {
      if (value) {
        callBack()// 如果value为true直接通过
      } else {
        callBack(new Error('您被坑就完事了'))
      }
    }
    return {
      loginForm: {
        mobile: '', // 手机号
        code: '', // 验证码
        check: false// 是否勾选协议
      },
      // 定义rules校验规则
      // key(字段名):value(数组=>多个 多个=>一个字段,可能有一个或者多个校验规则)
      loginRules: {
        mobile: [{
          required: true, // 意味着必填
          message: '手机号不能为空' // 如果没有满足要求,会提示message内容
        }, {
          pattern: /^1[3456789]\d{9}$/, // 正则表达式
          message: '手机号格式不正确'
        }],
        code: [{
          required: true,
          message: '验证码不能为空'
        }, {
          pattern: /^\d{6}$/, // 正则表达式
          message: '验证码必须为6位数字'
        }],
        // required只校验(空串)null,undefined,但不校验false,true
        check: [{
          validator
        }]
      }
    }
  },
  methods: {
    login () {
      // 通过el-form组件validata方法,校验整个表单数据
      // 传入一个回调函数
      this.$refs.loginForm.valuedate((isOk, obj) => {
        // if (isOk) {
        //   this.$message({ type: 'success', message: '成功' })
        // } else {
        //   this.$message({ type: 'warning', message: '失败' })
        // }
      })
    }
  }
}
</script>

<style lang='less' scoped>
//如果要用less/scss语言的话 需要给lang一个属性
//lang属性是对css进行语言指定
//scoped 只针对当前自己组件起作用
//100vh占据当前可视屏幕的100%
.login {
  background-image: url(../../assets/img/login_bg.jpg);
  height: 100vh;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
  .login-card {
    width: 440px;
    height: 300px;
    .logo {
      text-align: center;
      img {
        height: 45px;
        // width: 200px; 按比例缩放
      }
    }
  }
}
</style>
