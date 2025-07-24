<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Bai1 from './components/Bai1.vue'
import Bai2 from './components/Bai2.vue'
import Bai3 from './components/Bai3.vue'
import CreatePost from './components/CreatePost.vue'
import PostList from './components/PostList.vue'

import { ref } from 'vue'

const posts = ref([])
// Hàm này nhận bài viết mới và thêm vào danh sách
function addPost(post) {
  posts.value.push(post)
}
</script>

<template>
  <HelloWorld msg="33 Lê Nguyễn Hoàng Trung" />
  <Bai1/>
  <Bai2/>
  <Bai3/>

  <h2 class="mt-5 text-danger">Bài 4</h2>
  <CreatePost @add-post="addPost" />
  <PostList :posts="posts" />
</template>

<style scoped>

</style>
