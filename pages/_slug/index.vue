<template>
  <main class="main">
    <!-- <img :src="thumbnail && thumbnail.url"> -->
    <picture v-if="thumbnail">
    <source
    　media="(min-width: 768px)"
    　type="image/webp"
    　:srcset="`${thumbnail.url}?w=600&fm=webp, ${thumbnail.url}?w=1200&fm=webp 2x`"
    />
    <source
    　media="(max-width: 768px)"
    　type="image/webp"
    　:srcset="`${thumbnail.url}?w=375&fm=webp, ${thumbnail.url}?w=750&fm=webp 2x`"
    />
    <img :src="`${thumbnail.url}?w=1200`" class="thumbnail" alt/>
    </picture>

    <h1 class="title">{{ title }}</h1>
    <p class="publishedAt">{{ publishedAt }}</p>
    <p class="category">{{ category && category.name }}</p>
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