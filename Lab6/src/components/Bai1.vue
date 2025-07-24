<template>
    <h1 class="text-danger mt-5">Bài 1</h1>
    <div class="p-3 border rounded mb-4">
        <h4>Nhập điểm của bạn</h4>
    <input v-model.number="score" type="number" min="0" max="10" step="0.1" class="form-control mb-2" style="font-size:18px;" placeholder="Nhập điểm trung bình">
        <div class="border p-2 rounded">
            <span v-if="score < 0 || score > 10" class="text-danger">Điểm không hợp lệ!</span>
            <span v-else-if="score < 5">Yếu</span>
            <span v-else-if="score < 6.5">Trung bình</span>
            <span v-else-if="score < 8">Khá</span>
            <span v-else-if="score < 9">Giỏi</span>
            <span v-else="score">Xuất sắc</span>
        </div>
    </div>
</template>

<script setup>
    import {ref} from 'vue';
    const score = ref('');
</script>