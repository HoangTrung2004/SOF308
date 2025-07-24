<template>
    <div>
        <h2>Danh sách bài viết</h2>
        <div v-for="(post, index) in posts" :key="index" :class="{ 'highlighted': post.title.lenght > 20 }" 
            :style="{ backgroundColor: post.backgroundColor, color: post.textColor }">
            <h3 class="text-success">{{ post.title }}</h3>
            <h4 class="text-danger">{{ post.author }}</h4>
            <p > {{ post.content }}</p>
        </div>
    </div>
</template>

<script setup>
// Định nghĩa props (biến đầu vào) nhận từ component cha
defineProps({
  posts: {            
    type: Array,      
    required: true    
  }
});
</script>