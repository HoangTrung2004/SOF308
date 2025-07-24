<template>
    <h1 class="text-danger mt-5">Bài 2</h1>

    <div class="p-3 border rounded ">
        <h2>Nhập tháng:</h2> <br>
        <input v-model.number="month" type="number"  placeholder="Nhập tháng đi bạn eo" >
        <p v-if="month < 1 || month >12" class="text-danger">Vui lòng nhập từ tháng 1-12</p>
        <p v-else-if="month >= 1 && month <= 3">Mùa xuân</p>
        <p v-else-if="month <= 6">Mùa hạ</p>
        <p v-else-if="month <= 9">Mùa thu</p>
        <p v-else-if="month <= 12">Mùa đông</p>
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    const month = ref('');
</script>