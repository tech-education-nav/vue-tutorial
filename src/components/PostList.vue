<script setup>
import { computed, onBeforeMount, ref } from "vue";
import PostFilterInput from "./PostFilterInput.vue";
import Tooltip from "./common/Tooltip.vue";
// カスタムイベント
const emit = defineEmits(["select"]);
// 投稿一覧
const posts = ref([]);
// 絞り込み
const filterText = ref("");
const filteredPosts = computed(() => posts.value.filter((v) => v.title.includes(filterText.value)));
// 投稿一覧を取得する
const fetchPosts = async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts");
    posts.value = await response.json();
  } catch (error) {
    alert("不明なエラーが発生");
  }
};
// リスト選択
const handleClickPost = (post) => {
  emit("select", post);
};
onBeforeMount(() => {
  // DOMが表示される前に投稿データを取得する
  fetchPosts();
});
</script>

<template>
  <PostFilterInput v-model="filterText" placeholder="記事タイトルで絞り込み" />
  <h2>
    記事一覧
    <Tooltip> この機能は、ブログ記事の一覧を表示しています。 </Tooltip>
  </h2>
  <p v-if="filteredPosts.length === 0">記事はありません。</p>
  <ul>
    <li v-for="post in filteredPosts" :key="post.id" @click="handleClickPost(post)">
      {{ post.title }}
    </li>
  </ul>
</template>

<style scoped>
ul {
  padding: 0;
  margin: 0;
}
li {
  padding: 8px;
  list-style: none;
  border-top: 1px solid #ccc;
}
li:hover {
  cursor: pointer;
  background-color: #f8f8f8;
}
</style>
