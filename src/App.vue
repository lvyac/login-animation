<template>
  <LoginPage
    ref="loginRef"
    brand-name="管理系统"
    title="后台管理登录"
    subtitle="请输入您的登录信息"
    primary-color="#4f46e5"
    @submit="handleLogin"
  />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import LoginPage from './components/LoginPage.vue'

const loginRef = ref<InstanceType<typeof LoginPage>>()

async function handleLogin(payload: { username: string; password: string; remember: boolean }) {
  loginRef.value?.setLoading(true)

  // Replace with your real auth logic
  await new Promise(r => setTimeout(r, 500))

  if (payload.username === 'demo' && payload.password === '1234') {
    alert('登录成功！')
  } else {
    loginRef.value?.setError('用户名或密码错误')
  }

  loginRef.value?.setLoading(false)
}
</script>
