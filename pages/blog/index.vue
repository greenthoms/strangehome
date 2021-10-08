<template>
  <div>
    <div class="flex flex-col">
      <div v-for="(post, tags, index) in posts" :key="index">
        <nuxt-link :to="`/blog/${post.slug}`" class="px-4 py-4 relative block">
          <span class="underline">{{ post.title }}</span>
          <div class="flex flex-row flex-wrap text-xs">
            <div
              v-for="(tag, index) in post.tags"
              :key="index"
              class="text-xs mr-1 px-1 bg-green-600"
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
  name: 'BlogList',
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
