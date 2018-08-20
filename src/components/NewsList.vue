<template>
  <div class="newslist">
    <ul class="media-list">
      <li class="media" v-for="article in articles" >
        <div class="media-left">
          <a v-bind:href="article.url" target="_blank">
            <img class="media-object" v-bind:src="article.urlToImage" alt="">
          </a>
        </div>
        <div class="media-body">
          <h4 class="media-heading">
            <a v-bind:href="article.url" target="_blank">
              {{article.title}}
            </a>
          </h4>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'newslist',
  props: ['source'],
  data () {
    return {
      articles : []
    }
  },
  methods: {
    updateSource: function (source) {
      if (source) {
        this.$http.get('https://newsapi.org/v1/articles?source=' + source + '&apiKey=2f7c8826498f4cfb9bf209a30214e305')
        .then( response => {
          this.articles = response.data.articles
        })
      }
    }
  },
  created: function () {
    this.updateSource(this.source)
  },
  watch: {
    source: function (val) {
      this.updateSource(val)
    }
  }
}
</script>

<style scoped>

</style>
