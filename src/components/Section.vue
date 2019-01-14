<template>
  <div class="section">
    <div class="section__introduction section__background-image">
      <div class="section__greetings">
        <h1>Well hello there.</h1>
        <transition name="fade" id="about">
          <div v-if="show">
            <p>I'm Ryan Bazzana.</p>
            <p>I'm a full stack developer based out of Brisbane, Australia.</p>
            <a href="#tech">
              <button class="button">></button>
            </a>
          </div>
        </transition>
      </div>
    </div>
    <div class="section__tech" id="tech">
      <h2>Tech I love</h2>
      <p>While I'm quite experienced in developing for wordpress, my interest lies in javascript, specifically Vue.js</p>
      <p>Heres some neat tech I use</p>
      <div class="icons">oodles of icons</div>
    </div>
    <div class="section__interests" id="interests">
      <h2>CODE</h2>
      <p>When I'm not on my computer I like to spend time outdoors hiking, practicing photography or driving around twisty mountain roads (responsibly, of course).</p>
    </div>
    <div class="section__contact" id="contact">
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
      secondShow: false
    };
  },
  mounted() {
    setTimeout(() => {
      this.show = true;
    }, 2750);
  }
};
</script>

<style lang="scss">
.section {
  height: 100vh;
  display: block;
  width: 100vw;
  align-content: middle;

  &__greetings {
    margin-top: 30vh;

    h1 {
      position: relative;
      max-width: 250px;
      margin: 0 auto;
      border-right: 2px solid rgba(255, 255, 255, 0.75);
      font-size: 180%;
      text-align: center;
      white-space: nowrap;
      overflow: hidden;
      background: #000;

      transform: translateY(-75%);
      animation: typewriter 1.3s steps(17) 1s 1 normal both,
        blinkTextCursor 1s steps(17) infinite normal;

      @keyframes typewriter {
        from {
          max-width: 0;
        }
        to {
          max-width: 250px;
        }
      }
      @keyframes blinkTextCursor {
        from {
          border-right-color: rgba(255, 255, 255, 0.75);
        }
        to {
          border-right-color: transparent;
        }
      }
    }
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
.fade-enter-active {
  transition: all 0.8s ease;
}
.fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}
.fade-enter, .fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(30px);
  opacity: 0;
}
</style>
