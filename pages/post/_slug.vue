<template>
  <div class="container flex-col">
    <h1 class="text-4xl font-bold m-4">{{ doc.title }}</h1>
    <nuxt-content :document="doc" class="text-left" />
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
}
</script>

<style>
.nuxt-content > * {
  margin: 1em;
}

.nuxt-content > blockquote {
  margin-top: 10px;
  margin-bottom: 10px;
  margin-left: 50px;
  padding-left: 15px;
  border-left: 3px solid #ccc;
}
</style>
