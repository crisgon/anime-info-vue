<template>
  <div class="box">
    <img :src="img"/>
    <div class="info">
      <h3 class="info-title">{{ title }}</h3>
      <span class="info-airing">{{ release }}</span>
      <btn className="info" :linkTo="url">More Info</btn>
    </div>
    <div class="podium">
      <span class="podium-rank">{{ rank }}º</span>
      <span class="podium-score">Score: {{ score }}</span>
    </div>
  </div>
</template>

<script>
import btn from './Button';
export default {
  props: ['img', 'title', 'rank', 'score', 'release', 'url'],

  components: {
    btn
  }
}
</script>

<style scoped>
  .box {
    width: 450px;
    min-height: 160px;
    display: grid;
    grid-template-columns: 100px 2fr 1fr;
    box-sizing: border-box;
    padding: .5em;
    border-radius: 3px;
    box-shadow: 5px 5px 10px rgba(120,135,182,.1);
    background-color: #FCFCFC;
    color: #4F4F4F;
  }

  .info {
    grid-column: 2/3;
    box-sizing: border-box;
    padding-left: .5em;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  .info .info-airing {
    margin-bottom: .5em;
  }

  .podium {
    grid-column: 3/4;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
  }

  .podium-rank {
    box-sizing: border-box;
    padding: .5em 0;
    font-size: 3em;
    position: relative;
  }

  .podium-rank:after {
    content: '';
    width: 35px;
    height: 35px;
    background-image: url('./assets/chevron.svg');
    position: absolute;
    top: 10px;
    right: -35px;
  }

  .podium-score {
    position: relative;
  }

  .podium-score:after {
    content: '';
    width: 20px;
    height: 20px;
    background-image: url('./assets/star.svg');
    position: absolute;
    top: -2px;
    right: -22px;
  }
</style>

