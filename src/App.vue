<template>
  <div id="app">
    <h1>AnimeRank</h1>
    <ul>
      <li v-for="anime in animes">
        <box
          :img="anime.image_url"
          :title="anime.title"
          :release="anime.airing_start"
          :rank="anime.rank"
          :score="anime.score"/>
      </li>
    </ul>
  </div>
</template>

<script>
import box from './Box';
import axios from 'axios'
export default {
  components: {
    box
  },
  data() {
    return {
      animes: null
    }
  },
  mounted() {
    axios
      .get('https://api.jikan.moe/top/anime/1')
      .then(response => response)
      .then(r => this.animes = r.data.top);
  }
}
</script>

<style>

</style>
