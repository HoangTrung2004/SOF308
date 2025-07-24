<template>
        <h2 class="mt-5 text-danger">Bài 2</h2>
    <div >
        <input v-model="userInput" placeholder="Nhập dữ liệu vào đây" class="form-control mb-2" >
        <p>Giá trị nhập: {{ userInput }}</p>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    const userInput = ref('FPL');
</script>