<template>
  <div class="dve-login">
    <el-form class="login-from" :label-position="top" label-width="80px" :model="formdata">
      <h3>用户登录</h3>
      <el-form-item label="账号">
        <el-input v-model="formdata.username"></el-input>
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="formdata.password"></el-input>
      </el-form-item>
      <el-button type="primary" class="login-btn" @click.prevent="getList()">登录</el-button>
    </el-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      top: "top",
    /*登录数据*/ 
      formdata: {
        username: "",
        password: ""
      }
    };
  },
  methods: {
    async getList() {
      const res = await this.$http.post("login", this.formdata);
      console.log(res);
      const {
        data,
        meta: { msg, status }
      } = res.data;
      if (status === 200) {
        /*登录Token*/   
          localStorage.setItem('token',data.token)
        this.$router.push({ name: "home" })
        this.$message({
          message: `${msg}`,
          type: "success"
        });
      } else {
        this.$message.error(`${msg}`);
      }
    }
  }
};
</script>

<style>
.dve-login {
  height: 100%;
  background-color: #324152;
  display: flex;
  justify-content: center;
  align-items: center;
}
.dve-login .login-from {
  width: 400px;
  background-color: #fff;
  border-radius: 5px;
  padding: 30px;
}
.login-btn {
  width: 100%;
}
</style>
