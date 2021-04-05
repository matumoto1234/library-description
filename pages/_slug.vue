<template>
  <article>
    <div class="text-center">
      <h1>{{ page.title }}</h1>
      <p>作成日:{{ page.date }}</p>
      <h3>{{ page.description }}</h3>
    </div>
    <div class="leftright-margin">
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
  position: relative;
  padding: 1.5rem;
  text-align: center;
}

h1:before {
  position: absolute;
  bottom: 25px;
  left: calc(50% - 30px);
  width: 60px;
  height: 5px;
  content: '';
  border-radius: 3px;
  background: rgb(34, 12, 236);
}

h2 {
  color: #292929;
  background-color: #f7f5fd;
  border-left: 10px solid #6b13cf;
  padding: 10px;
  margin-top: 10px;
  margin-bottom: 10px;
}

.leftright-margin {
  margin-left: 150px;
  margin-right: 150px;
}
</style>
