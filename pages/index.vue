<template>
  <div>
    <div class="flex flex-row flex-wrap gap-4 m-4">
      <div
        v-for="(post, tags, tag, index) in posts"
        :key="index"
        class="font-semibold rounded-lg shadow-md text-white bg-purple-700 hover:bg-purple-900"
      >
        <nuxt-link :to="`/blog/${post.slug}`" class="p-4 relative block">
          <span class="underline">{{ post.title }}</span>
          <div class="flex flex-wrap">
            <div
              v-for="(tag, index) in post.tags"
              :key="index"
              class="text-xs mr-1 px-1 bg-purple-900"
            >
              {{ tag }}
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const page = await $content('index').fetch()
    const posts = await $content('blog').fetch()

    return {
      page,
      posts,
    }
  },
}
</script>

<style>
a:focus-visible {
  outline: -webkit-focus-ring-color auto 4px;
  outline-color: green;
  outline-style: auto;
  outline-width: 4px;
}
</style>
