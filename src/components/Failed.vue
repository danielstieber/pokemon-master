<template>
  <div class="wrapper">
    <p class="score_wording">{{score.success}} / {{numberOfQuestions}}</p>
    <div class="slogan">
      <span v-if="0 <= score.success && score.success <= 10">{{slogan.low}}</span>
      <span v-if="10 < score.success && score.success <= 20">{{slogan.medium}}</span>
      <span v-if="20 < score.success">{{slogan.high}}</span>
    </div>
    <router-link to="/">
      <button
        @click.native="restart()"
        class="wording nes-btn is-success restart_btn"
      >Restart</button>
    </router-link>
    <div class="failed_wrapper">
      <span>And I'm<img class="pokemon_img" :src="require('../assets/pokemons/' + `${test.obs_code}.png`)" alt=""><span class="keyword">{{test.name}}</span></span>
    </div>
    <div class="social_links">
      <!-- Sharing Button Facebook -->
      <a class="resp-sharing-button__link" href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fweichiachang.github.io%2Fpokemon-master%2F%23%2F" target="_blank" rel="noopener" aria-label="Facebook">
        <i class="nes-icon facebook"></i>
      </a>
      <!-- Sharing Button Twitter -->
      <a class="resp-sharing-button__link" href="https://twitter.com/intent/tweet/?text=Pokemon%20Master%20Guessing%20Game&amp;url=https%3A%2F%2Fweichiachang.github.io%2Fpokemon-master%2F%23%2F" target="_blank" rel="noopener" aria-label="Twitter">
        <i class="nes-icon twitter"></i>
      </a>
    </div>
    <img class="kumamon" src="../assets/kumamon.png" alt="">
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  name: 'Failed',
  props: {
    test: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  data () {
    return {
      slogan: {
        low: 'Wait ... what?',
        medium: 'What a pity',
        high: 'Awesomeeee!'
      }
    }
  },
  computed: {
    ...mapState({
      score: ({ score }) => score,
      numberOfQuestions: ({ numberOfQuestions }) => numberOfQuestions,
      currentFlag: ({ currentFlag }) => currentFlag,
    }),
  },
};
</script>

<style lang="scss" scoped>
.failed_wrapper {
  margin-top: 20px;
}
.pokemon_img {
  display: inline-block;
  width: 70px;
  vertical-align: bottom;
}
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  position: relative;
}
.slogan {
  font-size: 1.2rem;
  margin-top: 1rem;
  margin-bottom: 2rem;
}
.score_wording {
  font-size: 1.5rem;
  font-weight: bolder;
}
.restart_btn {
  font-size: 1rem;
  text-align: center;
  height: 50px;
  border-radius: 5px;
  margin-bottom: .3rem;
}

.social_links {
  margin-top: 1rem;
  margin-bottom: 7rem;
}

.kumamon {
  position: absolute;
  bottom: -5px;
  width: 300px;
}

// Basic Mobile Setting
@media only screen and (min-width: 320px) and (max-width: 479px) {
  .kumamon {
    width: 15rem;
  }
}
// For mobile (landscape)
@media only screen and (min-width: 480px) and (max-width: 767px) {
  .kumamon {
    width: 15rem;
  }
}

i {
  font-size: 4rem;
}

.keyword {
  font-weight: bolder;
  color: black;
  font-size: .8rem;
}

// Social Links
a {
  text-decoration: none !important;
}

.resp-sharing-button__link,
.resp-sharing-button__icon {
  display: inline-block
}

.resp-sharing-button__link {
  text-decoration: none;
  color: #fff;
  margin: .4em
}

.resp-sharing-button {
  border-radius: 5px;
  transition: 25ms ease-out;
  padding: 0.5em 0.75em;
}

.resp-sharing-button__icon svg {
  width: 1em;
  height: 1em;
  margin-right: 0.4em;
  vertical-align: top
}

.resp-sharing-button--small svg {
  margin: 0;
  vertical-align: middle;
}

/* Non solid icons get a stroke */
.resp-sharing-button__icon {
  stroke: #fff;
  fill: none
}

/* Solid icons get a fill */
.resp-sharing-button__icon--solid,
.resp-sharing-button__icon--solidcircle {
  fill: #fff;
  stroke: none;
  line-height: 15px;
  text-decoration: none;
}

.resp-sharing-button--twitter {
  background-color: #55acee
}

.resp-sharing-button--twitter:hover {
  background-color: #2795e9;
  text-decoration: none;
}

.resp-sharing-button--facebook {
  background-color: #3b5998
}

.resp-sharing-button--facebook:hover {
  background-color: #2d4373
}

.resp-sharing-button--tumblr {
  background-color: #35465C
}

.resp-sharing-button--tumblr:hover {
  background-color: #222d3c
}

.resp-sharing-button--reddit {
  background-color: #5f99cf
}

.resp-sharing-button--reddit:hover {
  background-color: #3a80c1
}

.resp-sharing-button--google {
  background-color: #dd4b39
}

.resp-sharing-button--google:hover {
  background-color: #c23321
}

.resp-sharing-button--linkedin {
  background-color: #0077b5
}

.resp-sharing-button--linkedin:hover {
  background-color: #046293
}

.resp-sharing-button--email {
  background-color: #777
}

.resp-sharing-button--email:hover {
  background-color: #5e5e5e
}

.resp-sharing-button--xing {
  background-color: #1a7576
}

.resp-sharing-button--xing:hover {
  background-color: #114c4c
}

.resp-sharing-button--whatsapp {
  background-color: #25D366
}

.resp-sharing-button--whatsapp:hover {
  background-color: #1da851
}

.resp-sharing-button--hackernews {
background-color: #FF6600
}
.resp-sharing-button--hackernews:hover, .resp-sharing-button--hackernews:focus {   background-color: #FB6200 }

.resp-sharing-button--vk {
  background-color: #507299
}

.resp-sharing-button--vk:hover {
  background-color: #43648c
}

.resp-sharing-button--facebook {
  background-color: #3b5998;
  border-color: #3b5998;
  color: white;
}

.resp-sharing-button--facebook:hover,
.resp-sharing-button--facebook:active {
  background-color: #2d4373;
  border-color: #2d4373;
}

.resp-sharing-button--twitter {
  background-color: #55acee;
  border-color: #55acee;
  color: white;
}

.resp-sharing-button--twitter:hover,
.resp-sharing-button--twitter:active {
  background-color: #2795e9;
  border-color: #2795e9;
}
</style>
