<template>
  <h1>GIF Seach App</h1>
  <Search @gifsFetched="onFetch" />
  <GifList :gifs="gifs" />
</template>

<script>
import Search from '@/components/Search.vue'
import GifList from '@/components/GifList.vue'
export default {
  name: 'App',
  components: { Search, GifList },
  data() {
    return {
      gifs: [],
    }
  },
  methods: {
    onFetch(result) {
      this.gifs = result
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
html, body {
  box-sizing: inherit;
}

body {
  background: #ecf0f1
}

#app {
  max-width: 800px;
  margin: 20px auto;
}

h1 {
  font-family: monospace;
  text-align: center;
  margin-bottom: 20px;
  color: #2980b9;
}
</style>
