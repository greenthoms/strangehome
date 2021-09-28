<template>
  <div class="px-4 prose w-screen">
    <nuxt-link to="/blog"><small>⇠ Back to index</small></nuxt-link>

    <h2>{{ post.title }}</h2>
    <p>{{ post.description }}</p>
    <nuxt-content :document="post" />
    <h3>Tags</h3>
    <ul>
      <li v-for="(tag, index) in post.tags" :key="index">
        <nuxt-link :to="`/tags/${tag}`">
          {{ tag }}
        </nuxt-link>
      </li>
    </ul>
    <nuxt-link to="/blog"><small>⇠ Back to index</small></nuxt-link>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params: { slug } }) {
    const post = await $content('blog', slug).fetch()
    return {
      post,
    }
  },
}
</script>
