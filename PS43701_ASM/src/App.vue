<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const user = ref(null)

// Hàm cập nhật user từ localStorage
function updateUserFromStorage() {
  const storedUser = localStorage.getItem('user')
  user.value = storedUser ? JSON.parse(storedUser) : null
}

// Chạy khi trang load
onMounted(() => {
  updateUserFromStorage()
})

// Cho phép các component khác gọi để cập nhật user ngay
window.updateUserGlobally = updateUserFromStorage

// Hàm đăng xuất
function logout() {
  localStorage.removeItem('user')
  user.value = null
  alert('Đã đăng xuất!')
  router.push('/login')
}
</script>

<template>
  <div class="container">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark px-3">
      <div class="container-fluid">
        <!-- Brand -->
        <router-link to="/" class="navbar-brand">Blog App</router-link>

        <!-- Phần menu bên phải -->
        <div class="d-flex align-items-center gap-3 ms-auto">
          <!-- Nếu chưa đăng nhập -->
          <template v-if="!user">
            <router-link to="/login" class="nav-link text-white">Login</router-link>
            <router-link to="/register" class="nav-link text-white">Register</router-link>
          </template>

          <!-- Nếu đã đăng nhập -->
          <template v-else>
            <router-link to="/profile" class="nav-link text-white">Profile</router-link>
            <span class="text-white">👋 Xin chào, {{ user.name }}</span>
            <button class="btn btn-outline-light btn-sm" @click="logout">Đăng xuất</button>
          </template>
        </div>
      </div>
    </nav>

    <!-- Nội dung chính -->
    <div class="container mt-4">
      <router-view />
    </div>
  </div>
</template>

<style scoped>
/* Có thể thêm CSS nếu cần */
</style>
