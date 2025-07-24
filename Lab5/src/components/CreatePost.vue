<template>
    <div class="p-3 border rounded mb-4">
        <h3 class="mb-3">Tạo bài viết mới</h3>
        <div class="mb-3">
            <input class="form-control" v-model="post.title" type="text" placeholder="Tiêu đề bài viết" />
        </div>
        <div class="mb-3">
            <input class="form-control" v-model="post.author" type="text" placeholder="Tên tác giả" />
        </div>
        <div class="mb-3">
            <textarea class="form-control" v-model="post.content" placeholder="Nội dung bài viết"></textarea>
        </div>
        <button class="btn btn-success" @click="submitPost">Đăng bài</button>
    </div>
</template>


<script setup>
import { reactive } from 'vue';
const emit = defineEmits(['add-post']) // Định nghĩa emit để gửi sự kiện ra component cha

// post là object reactive lưu thông tin bài viết đang nhậ
const post = reactive({
    title: '',
    author: '',
    content: ''
});

// // Hàm xử lý khi nút đăng bài
const submitPost = () => {
    if (post.title && post.author && post.content) {
        emit('add-post', { ...post })
        post.title = ''
        post.author = ''
        post.content = ''
    } else {
        alert("Vui lòng nhập đầy đủ ")
    }
}
</script>