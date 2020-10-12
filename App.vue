<template>
  <Layout>
    <template v-slot:header>
      Header
    </template>

    <template v-slot:sidebar>
      <div v-for="album in albums">
        {{ album.title }}
      </div>
      Sidebar
    </template>

    <template v-slot:content>
      Content
    </template>
  </Layout>
</template>

<script>
import Layout from './Layout.vue'

export default {
  components: {
    Layout
  },

  async created() { // fetching when first load
    this.$store.dispatch('albums/fetchAlbums')
  },

  mounted() {
     console.log(this.$store.state.albums.all)
  },

  computed: {
    albums() {
      return this.$store.state.albums.all
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
}
</style>