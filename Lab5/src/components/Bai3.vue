<template>
    <h2 class="mt-5 text-danger">Bài 3</h2>
    <div class="p-3 border rounded mb-4">
        <h1>Thông tin cá nhân</h1>
        <form >
            <div class="mb-3">
                <label >Họ và tên: </label>
                <input v-model="userInfo.userName" type="text" class="form-control" placeholder="Nhập họ và tên">
            </div>
            <div class="mb-3">
                <label >Tuổi: </label>
                <input v-model="userInfo.age" type="text" class="form-control" placeholder="Nhập tuổi của bạn">
            </div>
            <div class="mb-3">
                <label >Email </label>
                <input v-model="userInfo.email" type="text" class="form-control" placeholder="Nhập Email của bạn">
            </div>
        </form>
    </div>

    <!-- Hiển thị thông tin đã nhập -->
     <div class="bg-dark text-white rounded p-3 mt-4">
        <h2>Thông tin đã nhập: </h2>
        <p><b>Họ và tên:</b> {{ userInfo.userName }}</p>
        <p><b>Tuổi:</b> {{ userInfo.age }}</p>
        <p><b>Email:</b> {{ userInfo.email }}</p>
     </div>
</template>

<script setup>
import { reactive } from 'vue';

const userInfo = reactive ({
    userName: '',
    age: '',
    email: ''
});
</script>