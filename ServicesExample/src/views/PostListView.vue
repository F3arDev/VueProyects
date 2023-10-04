<template>
    <h3>Post List</h3>
    <ul>
        <li v-for="post in posts" :key="post.id">
            <Router-Link :to="{ name: 'PostDetail', params: { id: post.id } }">
                {{ post.title }}
            </Router-Link>

        </li>
    </ul>
</template>

<script setup>
import { RouterLink } from 'vue-router';
import postService from '../services/service';
import { onMounted } from 'vue';

const service = new postService();


const posts = service.getPosts();

onMounted(async () => {
    await service.fetchAll();
})

</script>

<style scoped></style>