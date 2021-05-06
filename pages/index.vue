<template>
  <div class="container">
    <a-card
      v-for="(item, index) in cardItem"
      :key="index"
      :title="item.title"
      :style="{ margin: '10px', height: '100%' }"
    >
      {{ item.data }}
      <nuxt-link
        :to="{ name: 'cardItem-slug', params: { slug: item.slug } }"
        type="primary"
        >Detail</nuxt-link
      >
    </a-card>
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
    query,
    req,
    res,
    redirect,
    error,
    $content,
  }) {
    const cardItem = await $content('cardItem').fetch()
    return {
      cardItem,
    }
  },
  methods: {},
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: top;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
