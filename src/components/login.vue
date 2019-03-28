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
    handleLogin () {
      this.$http.post(`login`, this.formdata)
        .then(err => {
          const {data:{data,meta:{msg,status}}} =err
           if(status===200){
               console.log('success--')
           }else{
               this.$message.error(msg);
           }
        })
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
