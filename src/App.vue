<script setup>
import { provide, ref } from "vue";
import PostList from "./components/PostList.vue";
import PostDetail from "./components/PostDetail.vue";

/**
 * 表示モード list or detail
 */
const displayMode = ref("list");
/**
 * 表示モード切り替え
 * @param {String} mode list or detail
 */
const changeMode = (mode) => {
  displayMode.value = mode;
};
/**
 * 詳細表示用の記事
 */
const detailPost = ref(null);
/**
 * リストがクリックされたら詳細を表示する
 * @param post 記事データ
 */
const viewDetail = (post) => {
  detailPost.value = post;
  displayMode.value = "detail";
};

/**
 * 投稿詳細をprovideする
 */
provide("detail-post", detailPost);
</script>

<template>
  <div class="wrapper">
    <PostList v-if="displayMode === 'list'" @select="viewDetail" />
    <PostDetail v-else-if="displayMode === 'detail'" @changeMode="changeMode" />
  </div>
</template>

<style scoped>
.wrapper {
  max-width: 1000px;
  margin: auto;
}
</style>
