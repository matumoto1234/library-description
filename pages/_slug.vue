<template>
  <article>
    <h1>{{ page.title }}</h1>
    <p>{{ page.date }}</p>
    <nuxt-content :document="page" />
  </article>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    const page = await $content('articles', params.slug).fetch()

    return {
      page
    }
  }
}
</script>
