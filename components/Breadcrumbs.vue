
<template>
  <ul class="news-item__breadcrumbs breadcrumbs">
    <li class="breadcrumbs__item">
      <nuxt-link to="/"  active-class="active" class="breadcrumbs__link">Главная</nuxt-link>
    </li>
    <li class="breadcrumbs__item">
      <nuxt-link to="/news" active-class="active" class="breadcrumbs__link">Новости</nuxt-link>
    </li>
    <li class="breadcrumbs__item">
      <nuxt-link exact to="/news/{slug}" active-class="active" class="breadcrumbs__link" >{slug}</nuxt-link>
    </li>
  </ul>
</template>

<style scoped>
  .breadcrumbs {
    padding: 0;
    margin: 0;
    margin-bottom: 32px;
    list-style: none;
    display: flex;
    gap: 20px;
  }

  .breadcrumbs__link {
    font-family: "Onest", sans-serif;
    font-size: 12px;
    font-weight: 500;
    text-transform: uppercase;
    line-height: 12px;
    color: #423F3F;
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
    background-color: #423F3F;
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




</style>
