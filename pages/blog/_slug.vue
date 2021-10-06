<template>
  <div>
    <nuxt-link to="/" class="btn btn-green">⇠ Go back</nuxt-link>
    <div class="p-4 my-4 prose w-screen">
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
    </div>
    <nuxt-link to="/" class="btn btn-green">⇠ Go back</nuxt-link>
  </div>
</template>

<style lang="postcss">
.btn {
  @apply px-6 py-2 mx-4 mt-8 text-sm rounded-lg shadow-md inline-block;
}
.btn-green {
  @apply text-white bg-green-500;
}
</style>

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
