<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">Nuxt SSR</a>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item">
          <nuxt-link exact no-prefetch active-class="active" class="nav-link" to="/">Home <span class="sr-only">(current)</span></nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" no-prefetch  class="nav-link" to="/about">About</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" no-prefetch  class="nav-link" to="/users">Users</nuxt-link>
        </li>
        <li class="nav-item" v-if="!hasToken">
          <nuxt-link active-class="active" no-prefetch  class="nav-link" to="/login">Login</nuxt-link>
        </li>
        <li class="nav-item"  v-else>
          <a @click.prevent="logout" class="nav-link" href="#">Logout</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
  export default {
    computed: {
      hasToken() {
        console.log(this.$store.getters.hasToken)
        return this.$store.getters.hasToken
    }
    },
    methods:{
      logout() {
        this.$store.dispatch('logout')
        this.$router.push('/login')
      }
    }
  }
</script>
