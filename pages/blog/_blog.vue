<template>
  <main>
    <section v-if="post">
      <nav class="mb-8 text-black" aria-label="go back">
        <router-back class="block" />
      </nav>

      <article>
        <h5
          v-if="post.createdAt"
          class="inline-block py-1 px-2 my-2 bg-gray text-black text-sm font-medium rounded-sm whitespace-no-wrap"
        >{{ formatDate(post.createdAt) }}</h5>
        <h1 class="text-black">{{ post.title }}</h1>
        <p class="mt-1 mb-4 text-black">{{ post.description }}</p>
        <nuxt-content class="text-black" :document="post" />
      </article>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("blog", params.blog).fetch();
    } catch (e) {
      error({ message: "Blog post not found" });
    }
    return { post };
  },
  methods: {
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString(process.env.lang) || ''
    }
  }
}
</script>
