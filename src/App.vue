<template>
  <div id="app" class="container">
    <SourceSelection v-on:sourceChanged="SourceChanged"></SourceSelection>
    <NewsList v-bind:source="source"></NewsList>
  </div>
</template>

<script>
import SourceSelection from './components/SourceSelection'
import NewsList from './components/NewsList'

export default {
  name: 'App',
  components: {
    SourceSelection,
    NewsList
  },
  data () {
    return {
      source: ""
    }
  },
  methods: {
    SourceChanged: function (source) {
      this.source = source;
    }
  }
}
</script>

<style>
#app {
}
</style>
