<script setup lang="ts">
// import { RouterLink, RouterView } from 'vue-router'
import {ref} from 'vue'

// 現在の日時
const now = new Date()

// 現在の日時の文字列を取得
const nowStr = now.toLocaleString()

// 現在の時刻文字列をテンプレート変数として用意
let timeStr = nowStr

// 同じく現在の時刻文字列をテンプレート変数としてref()で用意
const timeStrRef = ref(nowStr)

// 新しい時刻に変更する関数
function changeTime(): void {
  // 現在の日時を取得
  const newTime = new Date()
  // 現在の日時の文字列を取得
  const newTimeStr = newTime.toLocaleString()
  // 現在の時刻文字列をテンプレート変数に代入
  timeStr = newTimeStr
  // 同じく現在の時刻文字列をテンプレート変数としてref()で用意
  timeStrRef.value = newTimeStr
}

setInterval(changeTime, 1000)
</script>
<template>
  <p>現在時刻： {{ timeStr }}</p>
  <p>現在時刻(ref)： {{ timeStrRef }}</p>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
