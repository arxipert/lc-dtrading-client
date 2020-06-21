<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <nuxt-link class="navbar-brand" to="#">Navbar</nuxt-link>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item">
        <nuxt-link exact active-class="active" class="nav-link" to="/">Home <span class="sr-only">(current)</span></nuxt-link>
      </li>
      <li class="nav-item">
        <nuxt-link active-class="active" class="nav-link" to="/about">About</nuxt-link>
      </li>
      <li class="nav-item">
        <nuxt-link active-class="active" class="nav-link" to="/users">Users</nuxt-link>
      </li>
      <li class="nav-item" v-if="!hasToken">
        <nuxt-link active-class="active" class="nav-link" to="/login">Log in</nuxt-link>
      </li>
      <li class="nav-item" v-else>
        <a @click.prevent="logout" class="nav-link" href="#">Log out</a>
      </li>
    </ul>
  </div>
</nav>
</template>

<script>
export default {
  computed: {
    hasToken() {
      return this.$store.getters.hasToken
    }
  },
  methods: {
    logout() {
      this.$store.dispatch('logout');
      this.$router.push('login');
    }
  }
}
</script>