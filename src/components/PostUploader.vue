<script setup>
import { inject } from "vue";

/**
 * 投稿詳細をinjectで受け取る
 */
const detailPost = inject("detail-post");
</script>

<template>
  <div v-if="detailPost">投稿者: {{ detailPost.userId }}</div>
</template>
