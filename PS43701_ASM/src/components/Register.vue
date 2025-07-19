<template>
  <div class="card mx-auto" >
    <div class="card-body">
      <h3 class="card-title mb-3">Đăng ký tài khoản</h3>
      <form @submit.prevent="register">
        <div class="mb-3">
          <label class="form-label">Họ tên</label>
          <input v-model="form.name" type="text" class="form-control" required />
        </div>
        <div class="mb-3">
          <label class="form-label">Email</label>
          <input v-model="form.email" type="email" class="form-control" required />
        </div>
        <div class="mb-3">
          <label class="form-label">Mật khẩu</label>
          <input v-model="form.password" type="password" class="form-control" required />
        </div>
        <button class="btn btn-primary w-100" type="submit">Đăng ký</button>
      </form>
      <div class="mt-3 text-center">
        <router-link to="/login">Đã có tài khoản? Đăng nhập</router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const form = reactive({
  name: '',
  email: '',
  password: ''
})

function register() {
  let users = JSON.parse(localStorage.getItem('users') || '[]')
  const exists = users.find(u => u.email === form.email)
  if (exists) {
    alert('Email đã tồn tại!')
    return
  }

  users.push({ ...form })
  localStorage.setItem('users', JSON.stringify(users))
  alert('Đăng ký thành công!')
  router.push('/login')
}
</script>
