<template>
  <main class="main">
    <h1 class="title">{{ title }}</h1>
    <p class="publishedAt">{{ publishedAt }}</p>
    <div class="post" v-html="body"></div>
  </main>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData({ params }) {
  const { data } = await axios.get(
    `https://kaori-blog.microcms.io/api/v1/blog/${params.slug}`,
    {
      headers: { 'X-API-KEY': '5b89d763-7e27-445c-96b5-a6b5331176c0' }
    }
  )
  return data
  }
}
</script>