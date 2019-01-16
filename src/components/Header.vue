<template>
  <transition name="heightChange">
    <div class="header" :class="scrolled ? 'header--scrolled' : ''">
      <div class="header__photo">
        <img src>
      </div>
      <div class="header__left">
        <h1>Ryan Bazzana</h1>
      </div>
      <div class="header__right">
        <ul>
          <li>
            <a href="#tech">Tech</a>
          </li>
          <li>
            <a href="#interests">Interests</a>
          </li>
          <li>
            <a href="#contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      scrolled: false
    };
  },
  methods: {
    handleScroll() {
      this.scrolled = window.scrollY > 0;
    }
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  }
};
</script>

<style lang="scss">
.header {
  display: none;
  @media screen and (min-width: 768px) {
    display: block;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    max-width: 100%;
    margin: 0 auto;
    background-color: rgba(0, 0, 0, 0.3);
    color: #fff;
    z-index: 5;
    div {
      vertical-align: middle;
    }
  }
  &__photo {
    display: inline-block;
    img {
      position: relative;
      width: 100px;
      height: 100px;
      border-radius: 50%;
      display: inline-block;
      margin: 0px;
    }
  }
  &__left {
    display: none;
    @media screen and (min-width: 768px) {
      position: relative;
      height: 100%;
      display: inline-block;
      width: 25%;
      text-align: left;
      padding: 5px;
    }
  }
  &__right {
    position: relative;
    height: 100%;
    display: inline-block;
    width: 40%;
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      display: inline-block;
      margin: 0px;
      width: 33%;
    }
    a {
      font-size: 2vw;
      color: #919191;
      transition: all 0.3s ease;
      text-decoration: none;
      &:hover {
        color: #fff;
        font-size: 2vw;
        text-decoration: underline;
      }
    }
  }
}
.header--scrolled {
  position: fixed;
  height: 75px;
  top: 0;
  left: 0;
  right: 0;
}
.heightChange-enter-active,
.heightChange-leave-active {
  transition: height 1s ease-in-out;
  overflow: hidden;
}
.heightChange-enter,
.heightChange-leave-to {
  height: auto;
}
</style>
