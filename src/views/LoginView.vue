<template>
  <div id="bg"></div>
  <el-card class="center-card">
    <template #header>
      <div class="card-header">
        <h4>AB-OJ 在线考试平台</h4>
      </div>
    </template>
    
    <el-form :model="form" label-width="60px">
      <el-form-item label="用户名">
        <el-input v-model="form.username" />
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="form.password" type="password" />
      </el-form-item>
    </el-form>
    <template #footer><el-button type="primary" @click="onSubmit">点击登录</el-button></template>
  </el-card>
</template>

<script setup>
import { reactive } from "vue";
import service from "@/utils/request.js";
import { ElMessage } from 'element-plus'
const form = reactive({username:"",password:""})
const onSubmit = ()=>{
    console.log(form);
    service.post("/user/login", form).then(res => {
      console.log(res);
      ElMessage("登录成功");
    })
}

</script>

<style scoped>
  .center-card{
    border-radius: 10px;
    text-align: center;
    width: 45vh;
    height: 34vh;
    margin: 20vh auto 0;
    position: fixed;
    right: 200px;
    opacity: 0.8;
    background-color: rgb(216, 237, 220);
  }

  #bg{
    width: 100%;
    height: 100%;
    position: fixed;
    top:0;
    z-index: -1;
    background-image: url("/src/assets/bg.jpeg");
    background-size: cover;
  }
</style>
