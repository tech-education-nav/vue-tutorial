<script setup lang="ts">
import { ref } from "vue";
import PostList from "./components/PostList.vue";
import PostDetail from "./components/PostDetail.vue";

// 詳細表示用
const detailPost = ref(null);
// 表示モード 一覧 or 詳細
const displayMode = ref("list");
// 表示モード切り替え
const changeMode = (mode) => {
  displayMode.value = mode;
};
// リストがクリックされたら詳細を表示する
const viewDetail = (post) => {
  detailPost.value = post;
  displayMode.value = "detail";
};
</script>

<template>
  <div class="wrapper">
    <PostList v-if="displayMode === 'list'" @select="viewDetail" />
    <PostDetail
      v-else-if="displayMode === 'detail'"
      :detailPost="detailPost"
      @changeMode="changeMode"
    />
  </div>
</template>

<style scoped>
.wrapper {
  max-width: 1000px;
  margin: auto;
}
</style>
