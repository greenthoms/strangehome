<template>
  <div>
    <Hero
      :heading="page.heading"
      :subheading="page.subheading"
      :image="page.image"
    />
    <div class="flex flex-col">
      <div v-for="(post, tags, index) in posts" :key="index">
        <nuxt-link :to="`/blog/${post.slug}`" class="px-4 py-4 relative block">
          <span class="underline">{{ post.title }}</span>
          <div class="flex flex-row flex-wrap text-xs">
            <div class="bg-gray-100 px-1 mr-1 border">
              {{ post.tags[0] }}
            </div>
            <div class="bg-gray-100 px-1 mr-1 border">
              {{ post.tags[1] }}
            </div>
            <div class="bg-gray-100 px-1 mr-1 border">
              {{ post.tags[2] }}
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
