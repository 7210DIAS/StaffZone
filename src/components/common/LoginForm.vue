<template>
  <div class="login">
    <h2>Login</h2>

    <form @submit.prevent="handleLogin">
      <label>Email</label>
      <input v-model="email" type="email" required />

      <label>Password</label>
      <input v-model="password" type="password" required />

      <button type="submit" :disabled="loading">Login</button>
    </form>

    <p v-if="message" :class="{ error: !ok }">{{ message }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const email = ref('')
const password = ref('')
const message = ref('')
const ok = ref(false)
const loading = ref(false)

async function handleLogin() {
  message.value = ''
  ok.value = false
  loading.value = true

  try {
    const res = await axios.post('http://localhost:8080/api/login', {
      email: email.value,
      password: password.value
    })

    // backend returns { success: true/false, message, user? }
    if (res.data && res.data.success) {
      ok.value = true
      message.value = res.data.message || 'Logged in'
      // example: store user info in localStorage (quick demo)
      localStorage.setItem('user', JSON.stringify(res.data.user))
      // in real app: redirect to dashboard (router.push('/dashboard'))
    } else {
      ok.value = false
      message.value = res.data.message || 'Login failed'
    }
  } catch (err) {
    // axios throws on network error or non-2xx if thrown
    if (err.response && err.response.data && err.response.data.message) {
      message.value = err.response.data.message
    } else {
      message.value = 'Server error or cannot reach backend'
    }
  } finally {
    loading.value = false
  }
}
</script>
