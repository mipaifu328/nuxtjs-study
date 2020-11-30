<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        nuxt-about
      </h1>
      <div class="links">
        <h3>{{ name }}</h3>
        <h4>@{{ username }}</h4>
        <p>Email : {{ email }}</p>
        <p>
          <NuxtLink to="/">
            List of users
          </NuxtLink>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  validate({ params }) {
    return !isNaN(+params.id);
  },
  async asyncData({ $axios, params, error }) {
    try {
      const { data } = await $axios.get(`api/users/${+params.id}`);
      return data;
    } catch (e) {
      error({ message: "User not found", statusCode: 404 });
    }
  }
};
</script>

<style scoped></style>
