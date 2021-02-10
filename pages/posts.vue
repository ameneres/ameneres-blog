<template>
  <div class="container mx-auto max-w-screen-lg justify-start">
    <div class="py-4">
      <div class="flex flex-col text-left prose prose-lg">
        <h2 class="flex text-2xl items-center font-bold">
          <img
            class="h-4 w-4 mr-2"
            src="~/static/icon-calendar.svg"
            alt="calendar icon"
          />
          Daily
        </h2>
        <div class="flex flex-col px-8 pb-8 pt-2">
          <nuxt-link
            v-for="(post, index) in posts"
            :key="index"
            :to="`/post/${post.slug}`"
            class="py-4"
          >
            <h4 class="text-lg leading-6 font-medium text-gray-900 underline">
              {{ post.title }}
            </h4>
            <p class="mt-1 text-base text-gray-800">{{ post.description }}</p>
            <p class="text-xs mt-2 text-gray-800">
              {{ _dateFormat(post.date) }}
            </p>
          </nuxt-link>
          <nuxt-link to="/posts" class="text-sm font-bold mt-4">
            archive
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    let posts = await $content()
      .only(['title', 'slug', 'date', 'description'])
      .fetch()

    posts = posts.sort((a, b) => {
      return new Date(b.date) - new Date(a.date)
    })

    return { posts }
  },
  methods: {
    _dateFormat(date) {
      const d = new Date(date)
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return d.toLocaleDateString('en-US', options)
    },
  },
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
