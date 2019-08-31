<template>
  <div class="login">
      <el-card class='login-card'>
          <div  class="logo">
              <img src="../../assets/img/logo_index.pngs" alt="">
          </div>
          <!-- 表单组件 -->
          <el-form>
              <!-- 表单项 -->
              <el-form-item>
                  <!-- 放置组件内容 -->
                  <el-input></el-input>
              </el-form-item>
              <el-form-item>
                  <el-input style="width:280px"></el-input>
                  <el-button style="float:right">发送验证码</el-button>
              </el-form-item>
                <el-form-item>
                    <el-checkbox>我已阅读并同意用户协议和隐私条款</el-checkbox>
              </el-form-item><el-form-item>
                  <el-button type="primary" style="width:100%">登录</el-button>
              </el-form-item>
          </el-form>
      </el-card>
  </div>
</template>

<script>
export default {

}
</script>

<style lang='less' scoped>
//如果要用less/scss语言的话 需要给lang一个属性
//lang属性是对css进行语言指定
//scoped 只针对当前自己组件起作用
//100vh占据当前可视屏幕的100%
.login{
    background-image: url(../../assets/img/login_bg.jpg);
    height: 100vh;
    background-size: cover;
    display: flex;
    justify-content: center;
    align-items: center;
    .login-card{
        width: 440px;
        height: 300px;
        .logo{
            text-align: center;
            img{
                height: 45px;
                // width: 200px; 按比例缩放
            }
        }
    }
}
</style>
