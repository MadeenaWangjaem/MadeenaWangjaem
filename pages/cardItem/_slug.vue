<template>
  <div class="container">
    <h1>{{ item.title }}</h1>
    <h1>{{ item.data }}</h1>
    <nuxt-content :document="item"></nuxt-content>
  </div>
</template>
<script>
export default {
  async asyncData({
    isDev,
    route,
    store,
    env,
    params,

    $content,
  }) {
    const item = await $content('cardItem', params.slug).fetch()
    return {
      item,
    }
  },
}
</script>
<style scoped>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: top;
  text-align: center;
}
</style>
