<template>
  <div class="section">
    <div class="section__introduction section__background-image">
      <transition name="fade">
        <div v-if="show">
          <h1 class="section__greetings" v-if="show">Well hello there.</h1>
        </div>
      </transition>
      <transition name="fade">
        <div v-if="showSecond">
          <p>I'm Ryan Bazzana.</p>
          <p>I'm a full stack developer based out of Brisbane, Australia.</p>
        </div>
      </transition>
    </div>
    <div class="section__tech">
      <h2>Tech I love</h2>
      <p>While I'm quite experienced in developing for wordpress, my interest lies in javascript, specifically Vue.js</p>
      <p>Heres some neat tech I use</p>
      <div class="icons">oodles of icons</div>
    </div>
    <div class="section__interests">
      <h2>CODE&&CARS&&CAMERAS&&COFFEE</h2>
      <p>When I'm not on my computer I like to spend time outdoors hiking, practicing photography or driving around twisty mountain roads (responsibly, of course).</p>
    </div>
    <div class="section__contact">
      <h2>You can find me on my various social channels, just click below.</h2>
      <div class="icons">GitHub</div>
      <div class="icons">Instagram</div>
      <div class="icons">LnkedIn</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      showSecond: false
    };
  },
  methods: {
    displayText() {
      setTimeout(function() {
        this.show = true;
      }, 2000);
    }
  },
  mounted() {
    this.displayText;
  }
};
</script>

<style lang="scss">
.section {
  height: 120vh;
  display: block;
  width: 100vw;
  margin-top: 10vh;
  align-content: middle;
  h1 {
    text-align: left;
  }
  &__background-image {
    color: #fff;
    display: block;
    width: 100vw;
    height: 100vh;
    background: linear-gradient(rgba(0, 0, 0, 0.75), rgba(0, 0, 0, 0.75)),
      (url("../assets/body-bg.jpg"));
    overflow: hidden;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  &__section-overlay {
    height: 50vh;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
