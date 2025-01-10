<script setup>
import { inject } from "vue";
import PostUploader from "./PostUploader.vue";

/**
 * 投稿詳細をinjectで受け取る
 */
const detailPost = inject("detail-post");

// カスタムイベント
const emit = defineEmits(["changeMode"]);
</script>

<template>
  <div>
    <button @click="emit('changeMode', 'list')">一覧に戻る</button>
  </div>
  <div v-if="!detailPost">データがありません</div>
  <div v-else>
    <h2>記事詳細</h2>
    <hr />
    <PostUploader />
    <h1>{{ detailPost.title }}</h1>
    <p>{{ detailPost.body }}</p>
  </div>
</template>
