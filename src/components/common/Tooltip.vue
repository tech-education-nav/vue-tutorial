<template>
  <div class="tooltip-container">
    <button class="tooltip-trigger">？</button>
    <div class="tooltip-content">
      <slot />
    </div>
  </div>
</template>

<script setup></script>

<style>
.tooltip-container {
  position: relative;
  display: inline-block;
}
.tooltip-trigger {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background-color: blue;
  color: white;
  border: none;
  cursor: pointer;
}
/* ツールチップのスタイル */
.tooltip-content {
  position: absolute;
  min-width: 300px;
  top: 100%; /* トリガーの下に配置 */
  left: 50%;
  transform: translateX(-50%);
  background: #ccc;
  padding: 10px;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.2s ease, visibility 0.2s ease;
  z-index: 10;
}
/* ホバーでツールチップを表示 */
.tooltip-container:hover .tooltip-content,
.tooltip-content:hover {
  opacity: 1;
  visibility: visible;
}
</style>
