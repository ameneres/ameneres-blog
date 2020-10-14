<template>
  <div class="p-4 container mx-auto max-w-screen-lg justify-start">
    <div class="p-2 sm:p-4 md:p-8">
      <div class="text-left">
        <p class="">
          Hey! I'm António. I’m on a path to become a generalist.
        </p>
        <p>
          Learning to build products and turning them into businesses.
        </p>
        <p>
          Idea, design, code, marketing, sales, support.
        </p>
        <div class="my-8">
          <p>How I rate myself:</p>
          <ul>
            <li>- Programming: 2</li>
            <li>- Marketing: 2</li>
            <li>- Design: 1</li>
            <li>- Sales: 5</li>
            <li>- Copywrite: 1</li>
            <li>- User Experience: 1</li>
          </ul>
        </div>
      </div>
      <div class="flex flex-col text-left">
        <nav
          class="text-2xl leading-7 text-gray-900 sm:text-3xl sm:leading-9 sm:truncate"
        >
          <nuxt-link to="/" class="mr-4" exact>
            Latest
          </nuxt-link>
          <nuxt-link to="/projects" class="mr-4" exact>
            Projects
          </nuxt-link>
        </nav>
        <nuxt-link
          v-for="(post, index) in posts"
          :key="index"
          :to="`/post/${post.slug}`"
          class="py-4"
        >
          <h4 class="text-lg leading-6 font-medium text-gray-900 underline">
            {{ post.title }}
          </h4>
          <p></p>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    let posts = await $content().only(['title', 'slug', 'date']).fetch()

    posts = posts.sort((a, b) => {
      return new Date(b.date) - new Date(a.date)
    })

    return { posts }
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
