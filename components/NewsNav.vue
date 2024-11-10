<template>
  <div class="news-item__nav" :class="{ fixed: isNavFixed }">
    <div class="container">
      <ul class="news-item__breadcrumbs breadcrumbs" v-if="!isNavFixed">
        <li class="breadcrumbs__item">
          <nuxt-link to="/" active-class="active" class="breadcrumbs__link">
            Главная
          </nuxt-link>
        </li>
        <li class="breadcrumbs__item">
          <nuxt-link to="/news" active-class="active" class="breadcrumbs__link">
            Новости
          </nuxt-link>
        </li>
      </ul>
      <h2 class="breadcrumbs__item breadcrumbs__item--last" v-if="isNavFixed">
        <nuxt-link
          exact
          :to="`/news/${slug}`"
          active-class="active"
          class="breadcrumbs__link"
        >
          {{ slug }}
        </nuxt-link>
      </h2>
      <button class="news-item__close" @click="$router.push('/news')">
        <span class="visually-hidden">Закрыть.</span>
      </button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';

const isNavFixed = ref(false);
const navTop = ref(0);

const props = defineProps({
  slug: {
    type: String,
    required: true,
  },
});

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
</script>

<style scoped>
.news-item__nav {
  margin-bottom: 16px;
  padding-top: 16px;
  padding-bottom: 14px;
  position: relative;
  z-index: 10;
  transition: top 0.3s ease;
}

.news-item__nav.fixed {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: white;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  max-width: 1536px;
  width: calc(100% - 40px);
  padding-top: 26px;
  padding-bottom: 26px;
}

.breadcrumbs {
  padding: 0;
  margin: 0;
  list-style: none;
  display: flex;
  gap: 20px;
  width: calc(100% - 88px);
}

.breadcrumbs__link {
  font-family: "Onest", sans-serif;
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  line-height: 12px;
  color: #423f3f;
  text-decoration: none;
}

.breadcrumbs__item {
  position: relative;
}

.breadcrumbs__item::before {
  content: "";
  position: absolute;
  display: inline-block;
  width: 4px;
  height: 4px;
  background-color: #423f3f;
  top: 50%;
  left: -10px;
  transform: translateY(-50%);
  border-radius: 50%;
}

.breadcrumbs__item:first-child::before {
  display: none;
}

.active {
  opacity: 0.4;
}

.news-item__close {
  position: absolute;
  width: 88px;
  height: 80px;
  top: 0;
  right: 0;
  background-color: #ca2250;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  border: none;
  padding-right: 26px;
  border-top-right-radius: 16px;
  transition: width 0.3s ease;
}

.news-item__close::after {
    content: "";
    position: absolute;
    top: 0;
    right: 88px;
    display: block;
    background-image: url("../images/close-decor.svg");
    background-repeat: no-repeat;
    width: 60px;
    height: 80px;
    background-size: cover;
    z-index: 80;
  }

.news-item__close::before {
  content: "";
  display: block;
  background-image: url("../images/close-icon.svg");
  background-repeat: no-repeat;
  width: 56px;
  height: 56px;
  background-size: cover;
  z-index: 90;
}

.news-item__nav.fixed .breadcrumbs {
  width: calc(100% - 88px);
}

.news-item__nav.fixed .breadcrumbs__item--last {
  flex-grow: 1;
  margin: 0;
}

.breadcrumbs__item--last {
  display: block;
  width: 100%;
  padding: 0 10px;
  background-color: #fff;
  border-radius: 4px;
}

.breadcrumbs__item--last .breadcrumbs__link {
  display: inline-block;
}

@media (max-width: 1439px) {
  .news-item__nav.fixed {
    width: calc(100% - 40px);
    padding-top: 0;
    padding-bottom: 21px;
  }
}

@media (max-width: 1023px) {

  .news-item__nav.fixed {
    padding-top: 0;
    padding-bottom: 21px;
  }

  .news-item__close {
    width: 39px;
    height: 48px;
    padding-right: 14px;
  }

  .news-item__close::before {
    width: 19px;
    height: 19px;
  }

  .news-item__close::after {
      width: 45px;
      height: 48px;
      right: 30px;
    }

    @media (max-width: 767px) {
      .news-item__nav.fixed {
    width: calc(100% - 8px);
  }
    }
}
</style>
