<template>
  <div class="bg-white-100">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="max-w-2xl mx-auto   lg:max-w-none">
        <h2 class="text-2xl font-extrabold text-gray-900">
          Blog posts
        </h2>
        <div class="mt-6 space-y-12 lg:space-y-0 lg:grid lg:grid-cols-3 lg:gap-x-6">
          <div v-for="post in posts" :key="post.id" class="group relative">
            <NuxtLink :to="'/posts/'+post.id">
              <div class="relative w-full h-80 bg-white rounded-lg overflow-hidden group-hover:opacity-75 sm:aspect-w-2 sm:aspect-h-1 sm:h-64 lg:aspect-w-1 lg:aspect-h-1 mb-6">
                <img :src="post.image">
              </div>
              <p class="text-base font-semibold text-gray-900">
                {{ post.title }}
              </p>
              <h3 class="mt-6 text-sm text-gray-500 mb-6">
                <a href="#">
                  <span class="absolute inset-0" />
                  {{ post.description }}
                </a>
              </h3>
            </NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      posts: []
    }
  },
  async fetch () {
    this.posts = await fetch(
      'https://api.nuxtjs.dev/posts'
    ).then(res => res.json())
  }
}
</script>
