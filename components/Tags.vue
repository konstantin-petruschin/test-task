<template>
  <div class="news-item__tags tags">
    <nuxt-link to="" class="tags__item">В СМИ</nuxt-link>
    <nuxt-link to="" class="tags__item tags__item--promotions">акции</nuxt-link>
  </div>
</template>


<style>
  .tags {
    list-style: none;
    margin: 0;
    padding: 0;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .tags__item {
    border-radius: 20px;
    padding: 4px 12px;
    text-decoration: none;
    font-family: "Onest", sans-serif;
    font-weight: 400;
    font-size: 14px;
    line-height: 18px;
    color: #5b4481;
    border: 1px solid #5b4481;
  }

  .tags__item--promotions {
    position: relative;
    display: flex;
    gap: 4px;
    align-items: center;
    color: #ca2250;
    border-color: #ca2250;
  }

  .tags__item--promotions::before {
    content: "";
    background-image: url("../images/percent.svg");
    width: 13px;
    height: 13px;
    display: block;
    background-repeat: no-repeat;
    object-fit: cover;
  }

</style>
