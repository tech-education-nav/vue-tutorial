<script setup>
// Props
defineProps({
  detailPost: Object | null,
});
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
    <h1>{{ detailPost.title }}</h1>
    <p>{{ detailPost.body }}</p>
  </div>
</template>
