<template>
  <div class="layout">
    <el-container class="container">
      <el-header class="header" :gutter="24">
        <el-row>
          <el-col :span="4">
            <div class="grid-content bg-purple">
              <img src="../../assets/logo.png" alt :span="3">
            </div>
          </el-col>
          <el-col :span="19">
            <div class="grid-content bg-purple-light">
              <h3 :span="34" class="center">电商后台管理系统</h3>
            </div>
          </el-col>
          <el-col :span="1">
            <div class="grid-content bg-purple">
              <a href class="btn"
              @click="removeToken()">退出</a>
            </div>
          </el-col>
        </el-row>
      </el-header>
      <el-container>
        <el-aside class="aside" width="200px">
          <el-menu default-active="2" class="el-menu-vertical-demo" :unique-opened="true">
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>用户管理</span>
              </template>

              <el-menu-item index="1-1">
                <template slot="title">
                  <i class="el-icon-menu"></i>
                  <span>用户列表</span>
                </template>
              </el-menu-item>
            </el-submenu>
            <!-- er  -->
            <el-submenu index="2">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>用户权限</span>
              </template>

              <el-menu-item index="1-1">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>角色列表</span>
                </template>
              </el-menu-item>
              <el-menu-item index="1-2">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>权限列表</span>
                </template>
              </el-menu-item>
            </el-submenu>

            <!-- 三 -->
            <el-submenu index="3">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>商品管理</span>
              </template>

              <el-menu-item index="1-1">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>商品列表</span>
                </template>
              </el-menu-item>
              <el-menu-item index="1-2">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>分类参数</span>
                </template>
              </el-menu-item>
              <el-menu-item index="1-2">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>商品分类</span>
                </template>
              </el-menu-item>
            </el-submenu>
            <!-- 导航四 -->
            <el-submenu index="4">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>订单管理</span>
              </template>

              <el-menu-item index="1-2">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>订单列表</span>
                </template>
              </el-menu-item>
            </el-submenu>
            <!-- 导航五 -->
            <el-submenu index="5">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>数据统计</span>
              </template>

              <el-menu-item index="1-1">
                <template slot="title">
                  <i class="el-icon-location"></i>
                  <span>数据报表</span>
                </template>
              </el-menu-item>
            </el-submenu>
          </el-menu>
          <!--  -->
        </el-aside>
        <el-main class="main">Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  /*在创建vm实力之前调用钩子函数*/
  beforeCreate() {
    const token = localStorage.getItem("token");
    if (!token) {
      this.$router.push({ name: "login" });
    }
  }
,methods:{
    /*退出按钮功能*/ 
    removeToken(){
        // 退出提示
         this.$message.success('退出成功');
        //  清除本地存储
         localStorage.clear()
        /*返回登录页面*/  
         this.$router.push({name:'login'})
    }
}
};
</script>

<style>
.layout {
  height: 100%;
}
.container {
  height: 100%;
}
.header {
  background-color: #b3c0d1;
}
.aside {
  background-color: #d3dce6;
  /* height: 100%; */
}
.main {
  background-color: #e9eef3;
  /* height: 100%; */
}
.center {
  text-align: center;
  /* font-size: 24px; */
  box-sizing: border-box;
}
.btn {
  line-height: 55px;
  text-decoration: none;
}
</style>
