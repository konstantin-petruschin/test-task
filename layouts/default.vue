<template>

    <div class="news-item container">
      <Breadcrumbs/>
      <Tags/>
      <BodyNews/>
      <NextNews/>
    </div>

</template>

<style>
  *, *::after, *::before {
    box-sizing: border-box;
  }

  .container {
    box-sizing: border-box;
    max-width: 1540px;
    border-radius: 16px 16px 0 0;
    padding: 32px 240px 64px 240px;
  }

</style>

<script>
  import Breadcrumbs from '~/components/Breadcrumbs';
  import Tags from '~/components/Tags';
  import BodyNews from '~/components/BodyNews';
  import NextNews from '~/components/NextNews';
  export default {
    components: {
      Breadcrumbs,
      Tags,
      BodyNews,
      NextNews,
    }
  }
</script>
