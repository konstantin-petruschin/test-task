<template>
  <div v-if="news.value">
    <NewsNav :slug="$route.params.slug" />
    <Tags :tags="news.value.tags" />
    <BodyNews :news="news.value" />
    <NextNews :slug="nextNewsSlug" />
  </div>

  <div v-else-if="error.value">
    <p>Ошибка загрузки новости</p>
  </div>

  <div v-else>
    <p>Загрузка...</p>
  </div>
</template>



<style>
  body {
    margin: 0;
    padding: 0;
  }

  *, *::after, *::before {
    box-sizing: border-box;
  }

  img {
    width: 100%;
    height: auto;
    object-fit: cover;
    }

  .visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    margin: -1px;
    border: 0;
    padding: 0;
    white-space: nowrap;
    clip-path: inset(100%);
    clip: rect(0 0 0 0);
    overflow: hidden;
  }

  .popap-news {
    background-color:   rgba(66, 63, 63, 0.7);
  }

  .container {
    padding-left: 240px;
    padding-right: 240px;
  }

  .popap-news__content {
    padding: 10px 20px 0 ;
  }

  .news-item {
    position: relative;
    max-width: 1536px;
    border-radius: 16px 16px 0 0;
    margin: 0 auto;
    padding-bottom: 60px;
    background-color: #ffffff;
    z-index: 100;
    max-height: 100%;
    height: 100%;
  }



  @media (max-width: 1439px) {
    .container {
      padding-left: 120px;
      padding-right: 120px;
    }
  }

  @media (max-width: 1023px) {
    .container {
      padding-left: 40px;
      padding-right: 40px;
    }
  }

  @media (max-width: 767px) {
    .container {
      padding-left: 16px;
      padding-right: 16px;
    }


    .popap-news__content {
      padding: 7px 4px 0;
    }

    .news-item {
      padding: 0 0 60px;
    }
  }

</style>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { useFetch } from '#imports';
import NewsNav from '~/components/NewsNav.vue';
import Tags from '~/components/Tags.vue';
import BodyNews from '~/components/BodyNews.vue';
import NextNews from '~/components/NextNews.vue';

const isNavFixed = ref(false);
const navTop = ref(0);
const news = ref(null);
const nextNewsSlug = ref(null);

const { data, error } = useFetch(`https://bsk-admin-test.testers-site.ru/api/news/${$route.params.slug}`);

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  const navElement = document.querySelector('.news-item__nav');
  if (navElement instanceof HTMLElement) {
    navTop.value = navElement.getBoundingClientRect().top;
  }
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
});

const handleScroll = () => {
  isNavFixed.value = window.scrollY >= navTop.value;
};

if (data.value) {
  news.value = data.value;

  if (data.value.allNews) {
    const currentIndex = data.value.allNews.findIndex(item => item.slug === $route.params.slug);
    if (currentIndex > -1 && currentIndex < data.value.allNews.length - 1) {
      nextNewsSlug.value = data.value.allNews[currentIndex + 1].slug;
    }
  }
} else if (error.value) {

  console.error("Ошибка загрузки новости:", error.value);
}
</script>

