<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
            <Nuxt-link exact no-prefetch active-class='active' class="nav-link" to='/'>
                Home
            </Nuxt-link>
            <Nuxt-link active-class='active' class="nav-link" to='/about'>
                About
            </Nuxt-link>
            <Nuxt-link active-class='active' class="nav-link" to='/users'>
                Users
            </Nuxt-link>
            <Nuxt-link v-if="!hasToken" active-class='active' class="nav-link" to='/login'>
                Login
            </Nuxt-link>
            <a v-else @click.prevent="logout" class="nav-link" href="#">
                Logout
            </a>
        </div>
        </div>
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
      this.$store.dispatch('logout')
      this.$router.push('/login')
    }
  }
}
</script>