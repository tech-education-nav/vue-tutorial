<script setup>
import { inject } from "vue";
import PostUploader from "./PostUploader.vue";
import Tooltip from "./common/Tooltip.vue";

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
    <h2>
      記事詳細
      <Tooltip>
        <p>この機能は、ブログ記事の詳細を表示しています。</p>
        <p>詳しくはマニュアルをご覧ください。</p>
        <a href="https://example.com/" target="_blank">マニュアルを見る</a>
      </Tooltip>
    </h2>
    <hr />
    <PostUploader />
    <h1>{{ detailPost.title }}</h1>
    <p>{{ detailPost.body }}</p>
  </div>
</template>
