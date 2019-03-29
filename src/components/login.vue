<template>
    <div class="login-wrap">
        <el-form class="login-form" label-position="top" label-width="80px" :model="formdata">
        <h2>登录组件</h2>
            <el-form-item label="用户名">
              <el-input v-model="formdata.username"></el-input>
            </el-form-item>
            <el-form-item label="密码">
              <el-input v-model="formdata.password"></el-input>
            </el-form-item>
        <el-button
        @click.prevent=handleLogin()
        class="login-btn" type="success">成功按钮</el-button>
        </el-form>
    </div>
</template>

<script>
export default {
  data () {
    return {
      formdata: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    async handleLogin () {
      const res =await this.$http.post(`login`, this.formdata)
      console.log(res)
      const {data:{data,meta:{msg,status}}} =res
      if(status==200){
        localStorage.setItem('token',data.token)
        // 目的:渲染新组件 <-改标识 <-(js改标识)
        this.$router.push({
          path:'/'
        })
      }else{
        // 提示框 <- ui
        this.$message.error(msg);
      }
        // 处理异步操作的结果res
        // .then(response => {
        //   const {data:{data,meta:{msg,status}}} =response
        //    if(status===200){
        //      渲染home.vue <- 改标识 <- js改标识
        //        this.$router.push({
        //            path:'/'
        //        })
        //    }else{
        //        this.$message.error(msg);
        //    }
        // })
        const aa =localStorage.getItem('token')
        console.log(aa)
    }
  }
}
</script>

<style>
.login-wrap{
    height:100%;
    background: #324152;
    display:flex;
    justify-content:center;
    align-items: center
}
.login-form{
    background: #ffffff;
    border-radius: 5px;
    width: 400px;
    padding:30px
}
.login-btn{
    width:100%
}
</style>
