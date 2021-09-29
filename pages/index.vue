<template>
  <div>
    <div class="flex flex-col">
      <div v-for="(post, tags, tag, index) in posts" :key="index">
        <nuxt-link
          :to="`/blog/${post.slug}`"
          class="my-1 mx-4 px-4 py-4 relative block bg-purple-100 hover:bg-purple-300 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:ring-opacity-50"
        >
          <span class="underline">{{ post.title }}</span>
          <div class="flex flex-wrap">
            <div
              v-for="(tag, index) in post.tags"
              :key="index"
              class="text-xs mr-1 px-1 border light-blue-400"
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
