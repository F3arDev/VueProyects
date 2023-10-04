<template>
    <h3>Post Detail</h3>
    <div>
        <h3>{{ post.title }}</h3>
        <p>{{ post.body }}</p>
        <Router-Link :to="{ name: 'PostList' }">Volver atras</Router-Link>
    </div>
</template>

<script setup>
import postService from '../services/service';
import { RouterLink, useRoute } from 'vue-router';
import { onMounted } from 'vue';

const service = new postService();

const post = service.getpost();

onMounted(async ()=>{
    const route = useRoute()
    let elm = route.params.id
    await service.fetchById(elm)
})
</script>



<style scoped></style>