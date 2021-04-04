<template>
  <article>
    <div class="text-center">
      <h1>{{ page.title }}</h1>
      <p>作成日:{{ page.date }}</p>
      <h3>{{ page.description }}</h3>
      <nuxt-content :document="page" />
    </div>
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

<style>
.theme--light.v-application code {
  all: unset
}

h1 {
  font-size: 70px;
}

h2 {
  font-size: 50px;
}
</style>
