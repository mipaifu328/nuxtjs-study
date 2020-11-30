<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        nuxt-demo
      </h1>
      <div class="links">
        <nuxt-link to="/about" class="button--green">About</nuxt-link>
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>

      <div class="list">
        <el-button type="primary" v-for="user in users" :key="user.id" >
          <NuxtLink :to="'/users/'+user.id">
            {{ user.name }}
          </NuxtLink>
        </el-button>
      </div>
    </div>
  </div>
</template>

<script>
// import axios from 'axios' // 也可以通过这种方式调用axios
export default {
  async asyncData ({$axios}) {
    const { data } = await $axios.get('/api/users')
    return { users: data }
  },
}
</script>
<style scoped>
</style>
