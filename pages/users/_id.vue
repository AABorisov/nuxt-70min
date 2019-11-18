<template>
  <section>
    <h1>{{user.name}}</h1>

    <hr>

    <h3>{{user.email}}</h3>
  </section>
</template>

<script>
  export default {
    validate({params: { id }}) {
      return /^\d+$/.test(id)
    },
    async asyncData({$axios, params}) {
      const user = await $axios.$get(`https://jsonplaceholder.typicode.com/users/${params.id}`)
      return {user}
    }
  }
</script>
