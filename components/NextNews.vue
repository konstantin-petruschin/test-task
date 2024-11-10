<template>
  <div class="container">
    <div class="news-item__next news-next" v-if="slug">
      <a :href="`/news/${slug}`" class="news-next__link">
        <span class="visually-hidden">Следующая новость.</span>
        <img src="../images/img.png" alt="news-next__image" class="news-next__image">
        <div class="news-next__text-wrapper">
          <p class="news-next__title">Читать следующую новость</p>
        </div>
      </a>
    </div>
  </div>
</template>

<script lang="ts" setup>
const props = defineProps({
  slug: {
    type: String,
  },
});
</script>

<style>

  .news-next {
    padding: 4px;
    background-color:  #d9d9d9;
    border-radius: 16px;
    display: flex;
    gap: 25px;
    position: relative;
  }

  .news-next::before {
    content: "";
    position: absolute;
    display: block;
    width: 138px;
    height: 128px;
    background-image: url("../images/mask-news.svg");
    background-repeat: no-repeat;
    background-size: cover;
    top: 0;
    right: -1px;
  }



  .news-next img {
    width: 100%;
    height: auto;
    border-radius: 24px;
    object-fit: cover;
}


  .news-next__text-wrapper {
    padding-top: 16px;
    padding-bottom: 16px;
    display: flex;
    flex-direction: column;
  }

  .news-next__title {
    margin: 0;
    padding: 0;
    margin-bottom: 10px;
    max-width: calc(100% - 110px);
    font-weight: 700;
    font-size: 24px;
    color: #423f3f;
    font-weight: 700;
    font-family: "Unbounded" ,sans-serif;
  }

  .news-next__tags {
    margin-top: auto;
  }

  .news-next__tags .tags {
    margin-bottom: 0;
    padding: 0;
  }

  .news-next__link {
    position: absolute;
    top: 0;
    right: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 24px;
    width: 80px;
    height: 80px;
    box-shadow: 0 4px 12px 0 rgba(30, 26, 35, 0.05), 0 2px 6px 0 rgba(89, 18, 115, 0.1), 0 1px 2px 0 rgba(62, 74, 89, 0.02);
    padding: 23px;
    background-color: #ffffff;
    align-self: flex-end;
  }

  .news-next__link::after {
    content: "";
    background-image: url("../images/next-icon.svg");
    background-repeat: no-repeat;
    background-size: contain;
    display: block;
    width: 36px;
    height: 24px;
  }

  @media (max-width: 1023px) {

    .news-next::before {
      width: 123px;
      height: 113px;
    }

    .news-next__title {
      font-size: 14px;
      line-height: 16px;
      max-width: calc(100% - 75px);
    }

    .news-next__image {
      max-width: unset;
      border-radius: 16px;
    }

    .news-next__link {
      width: 65px;
      height: 65px;
      border-radius: 16px;
    }

    .news-next__link::after {
      height: 14px;
    }
}

  @media (max-width: 767px) {
    .news-next {
      flex-direction: column;
    }

    .news-next::before {
      width: 80px;
      height: 68px;
      top: unset;
      bottom: 4px;
      transform: rotate(90deg) translateY(-5px);
    }

    .news-next img {
      width: 100%;
      height: auto;
      object-fit: contain;
 }

    .news-next__text-wrapper {
      padding: 0 16px 16px;
    }

    .news-next__title {
      max-width: calc(100% - 40px);
    }

    .news-next__link {
      top: unset;
      bottom: 0;
      width: 45px;
      height: 45px;
      padding: 4px;
    }

    .news-next__link::after {
      width: 20px;
      transform: rotate(-45deg);
    }
  }




</style>
