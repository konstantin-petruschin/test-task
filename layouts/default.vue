<template>
  <div class="popap-news">
    <div class="popap-news__content" :style="{ paddingTop: isNavFixed ? '7px 4px 0' : '23px 4px 0' }">
      <div class="popap-news__item news-item">
        <NewsNav/>
        <Tags/>
        <BodyNews/>
        <NextNews/>
      </div>
    </div>
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

<script>
  import NewsNav from '~/components/NewsNav';
  import Tags from '~/components/Tags';
  import BodyNews from '~/components/BodyNews';
  import NextNews from '~/components/NextNews';

  export default {
    components: {
      NewsNav,
      Tags,
      BodyNews,
      NextNews,
    }
  }
</script>
