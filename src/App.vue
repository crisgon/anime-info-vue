<template>
  <div id="app">

    <h1>AnimeRank</h1>

    <ul class="animeRank">
      <li v-for="anime in animes">
        <box
          :img="anime.image_url"
          :title="anime.title"
          :release="anime.airing_start"
          :rank="anime.rank"
          :score="anime.score"/>
      </li>
    </ul>

    <div class="control">
      <div class="control-prev" @click="prevPage()" v-show="page != 1">Prev</div>
      <div class="control-next" @click="nextPage()" >Next</div>
    </div>

  </div>
</template>

<script>
import box from './Box';
import axios from 'axios';
export default {
  components: {
    box
  },
  data() {
    return {
      animes: null,
      page: 1
    }
  },
  created(){
    this.getAnimes();
  },
  methods: {
    getAnimes() {
      axios
        .get(`https://api.jikan.moe/top/anime/${this.page}`)
        .then(response => response)
        .then(r => {
          this.animes = r.data.top;
        });
    },
    nextPage() {
      this.page++;
      this.getAnimes();
    },

    prevPage() {
      this.page--;
      this.getAnimes();
    }
  }
}
</script>

<style>
  .animeRank {
    width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  .animeRank li {
    list-style: none;
    margin: .5em 0;
  }
    .control {
    width: 200px;
    margin: 10px auto;
    display: flex;
    justify-content: space-around;
  }

  .control-prev,
  .control-next {
    box-sizing: border-box;
    padding: .5em;
    background-color: #FCFCFC;
    color: #4F4F4F;
    box-shadow: 5px 5px 10px rgba(120,135,182,.1);
    transition: all .3s;
  }

  .control-prev:hover,
  .control-next:hover {
    cursor: pointer;
    transform: translateY(-5px);
  }
</style>
