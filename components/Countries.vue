<template>
  <p v-if="$fetchState.pending">Fetching mountains...</p>
  <p v-else-if="$fetchState.error">An error occurred :(</p>
  <div v-else>
    <h1>REST Countries Name</h1>
    <ul>
      <li v-for="country of name">{{ country.title }}</li>
    </ul>
    <button @click="$fetch">Refresh</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        countries: []
      }
    },
    async fetch() {
      this.mountains = await fetch(
        'https://restcountries.com/v2/all'
      ).then(res => res.json())
    }
  }
</script>