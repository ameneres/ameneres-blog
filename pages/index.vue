<template>
  <div class="p-2">
    <div class="grid grid-cols-1 gap-4 sm:grid-cols-4 sm:p-4 md:p-16">
      <div
        class="col-span-1 sticky bg-green-400 border-solid border-black border-2 p-4 sm:p-8"
        style="box-shadow: 0px 4px 0px #000000;"
      >
        <p class="">
          Hey! I'm António.
        </p>
        <p>
          I’m on a path to become a generalist.
        </p>
        <p>
          Learning to become a product builder.
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
      <div class="col-span-3 flex flex-col">
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
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

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
