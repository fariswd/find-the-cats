<template lang="html">
  <div id="home">
    <h1>Home</h1>
    <md-card v-for="cat in latestCats" :key="cat['.key']">
      <md-card-media>
        <img :src="cat.url" :alt="cat.comment">
      </md-card-media>

      <md-card-header>
        <div class="md-title">{{ cat.comment }}</div>
      </md-card-header>

      <md-card-actions>
        <router-link :to="{ path: '/detail/'+cat['.key'], params: {} }">
          <md-button>Details</md-button>
        </router-link>
      </md-card-actions>
    </md-card>
  </div>
</template>

<script>
export default {
  firebase: function () {
    return {
      cats: this.$db.ref('cats')
    }
  },
  computed: {
    latestCats: function () {
      console.log(this.cats)
      return this.cats.reverse()
    }
  }
}
</script>

<style lang="css">
.md-card {
  margin-bottom: 16px;
}
</style>
