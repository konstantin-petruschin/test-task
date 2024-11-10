<template>
  <div class="news-item__body-news body-news container">
    <p class="body-news__title">{{ news.title }}</p>
    <time :datetime="news.published_at" class="body-news__date">{{ news.published_at }}</time>
    <div v-html="news.content" class="body-news__text"></div>
  </div>
</template>

<script lang="ts" setup>
const props = defineProps({
  news: {
    type: Object,
    required: true,
  },
});
</script>

<style>

  .body-news {
    position: relative;
  }

  .body-news__title {
    margin: 0;
    padding: 0;
    margin-bottom: 20px;
    font-family: "Unbounded", sans-serif;
    font-weight: 700;
    font-size: 48px;
    line-height: 56px;
    text-wrap: balance;
  }

  .body-news__date {
    color: #cfcfcf;
    font-weight: 500;
    font-size: 16px;
    font-family: "Onest", sans-serif;
    margin-bottom: 30px;
    display: block;
  }

  .body-news__text {
    margin: 0;
    padding: 0;
    font-family: "Onest", sans-serif;
    font-weight: 400;
    line-height: 20px;
    font-size: 16px;
    color: #717070;
    margin-bottom: 65px;
  }

  @media (max-width: 1023px) {
    .body-news__title {
      font-size: 24px;
      line-height: 28px;
    }

  }

</style>
