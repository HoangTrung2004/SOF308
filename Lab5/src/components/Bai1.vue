<template>
    <h2 class="mt-5 text-danger"  >Bài 1</h2>
    <div class="p-1">
        <p> {{ message }}</p>
        <button class="btn btn-dark" @click="UpdateMessage"> Thay đổi thông điệp </button>
    </div>

    <button @click="myClick">
        <span v-if="ok">Ẩn</span>
        <span v-else>Hiện</span>
    </button>
    <p v-show="ok">Hiển thị</p>
</template>

<script setup>
    import { ref } from 'vue'; // Import ref để tạo biến (nhiều thuộc tính thì import reactive)  
    const message = ref("Thông điệp ban đầu");
    const UpdateMessage = () => {
        message.value = "Thông điệp đã được thay đổi"
    };

    const ok = ref("true");
    const myClick = () => {
        ok.value = !ok.value;
    }
</script>