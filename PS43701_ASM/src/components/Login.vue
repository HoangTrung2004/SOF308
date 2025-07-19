<template>
  <div class="container">
    <div class="card mx-auto" style="max-width: 500px">
      <div class="card-body">
        <h3 class="card-title mb-3">Đăng nhập</h3>
        <form @submit.prevent="login">
          <div class="mb-3">
            <label class="form-label">Email</label>
            <input v-model="form.email" type="email" class="form-control" required />
          </div>
          <div class="mb-3">
            <label class="form-label">Mật khẩu</label>
            <input v-model="form.password" type="password" class="form-control" required />
          </div>
          <button class="btn btn-success w-100" type="submit">Đăng nhập</button>
        </form>
        <div class="mt-3 text-center">
          <router-link to="/register">Chưa có tài khoản? Đăng ký</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const form = reactive({
  email: '',
  password: ''
})

function login() {
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const user = users.find(u => u.email === form.email && u.password === form.password)

  if (user) {
    localStorage.setItem('user', JSON.stringify(user))
    alert('Đăng nhập thành công!')

    // Gọi hàm cập nhật user ở App.vue
    if (window.updateUserGlobally) {
      window.updateUserGlobally()
    }

    router.push('/') // Quay về trang chủ
  } else {
    alert('Sai email hoặc mật khẩu!')
  }
}
</script>
