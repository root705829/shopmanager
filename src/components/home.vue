<template>
  <el-container class="container">
    <el-header>
      <el-row>
        <el-col :span="4">
          <img src="@/assets/logo.png" alt="图片加载失败">
        </el-col>
        <el-col :span="19" class="middle">
          <h2>电商后台管理系统</h2>
        </el-col>
        <el-col :span="1">
          <a href="#" class="logout" @click="handleLogout">退出</a>
        </el-col>
      </el-row>
    </el-header>
    <el-container>
      <el-aside class="aside" width="200px">
              <el-menu
      :unique-opened='true'
      :router="true"     
      default-active="2"
      class="el-menu-vertical-demo"
      >
        <!-- 1 -->
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>用户管理</span>
        </template>
          <el-menu-item index="users">
              <i class="el-icon-menu"></i>
              <span>用户列表</span>
          </el-menu-item>
      </el-submenu>
        <!-- 2 -->
      <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>权限管理</span>
        </template>
          <el-menu-item index="2-1">
              <i class="el-icon-menu"></i>
              <span>角色列表</span>
          </el-menu-item>
          <el-menu-item index="2-2">
              <i class="el-icon-menu"></i>
              <span>权限列表</span>
          </el-menu-item>
      </el-submenu>
        <!-- 3 -->
      <el-submenu index="3">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>商品管理</span>
        </template>
          <el-menu-item index="2-1">
              <i class="el-icon-menu"></i>
              <span>商品列表</span>
          </el-menu-item>
          <el-menu-item index="2-2">
              <i class="el-icon-menu"></i>
              <span>分类参数</span>
          </el-menu-item>
          <el-menu-item index="2-3">
              <i class="el-icon-menu"></i>
              <span>商品管理</span>
          </el-menu-item>
      </el-submenu>
        <!-- 4 -->
      <el-submenu index="4">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>订单管理</span>
        </template>
          <el-menu-item index="2-1">
              <i class="el-icon-menu"></i>
              <span>订单列表</span>
          </el-menu-item>
      </el-submenu> 
       <!-- 5 -->
      <el-submenu index="5">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>数据统计</span>
        </template>
          <el-menu-item index="2-1">
              <i class="el-icon-menu"></i>
              <span>数据报表</span>
          </el-menu-item>
      </el-submenu> 
    </el-menu>
      </el-aside>
      <el-main class="main">
          <router-view></router-view>
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
    
        // beforeCreate() {
        //     console.log(11111)
        //     if(!localStorage.getItem('token')) {
        //         this.$router.push({
        //             // name:"Login"
        //             path:'/login'
        //         })
        //     }
        // },
        beforeMount() {
            console.log(111)
            if (!localStorage.getItem("token")) {
                this.$router.push({
                    name: "login"
                });
                this.$message.warning("请先登录");
            }
        },
        methods:{
            handleLogout() {
                localStorage.clear()
                this.$router.push({
                    path:'/login'
                })
                this.$message.warning('您已退出')
            }
        }
    }

</script>

<style>
.container {
  height: 100%;
  background-color: #b3c0d1;
}
.middle{
    line-height: 60px;
    text-align: center;
    color:#fff
}
.aside {
  background-color: yellow;
}
.main {
  background-color: green;
}
.logout{
    line-height: 60px;
    text-decoration: none;
}
</style>
