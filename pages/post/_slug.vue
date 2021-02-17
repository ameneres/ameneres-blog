<template>
  <div class="container flex-col max-w-screen-md justify-center mx-auto">
    <h1 class="text-4xl font-bold m-4">{{ doc.title }}</h1>
    <nuxt-content :document="doc" class="prose" />
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params }) {
    const doc = await $content(params.slug).fetch()

    return {
      doc,
    }
  },
  head() {
    return {
      title: this.doc.title,
      link: [
        {
          rel: 'canonical',
          href: `https://ameneres.com/post/${this.doc.title}`,
        },
      ],
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: this.doc.description,
        },
      ],
    }
  },
}
</script>

<style>
.nuxt-content > * {
  margin: 1em;
}

.nuxt-content blockquote {
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 50px;
  padding-left: 15px;
  border-left: 3px solid #ccc;
}

.nuxt-content a {
  text-decoration: underline;
}
</style>
