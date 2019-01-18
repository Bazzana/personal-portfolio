<template>
  <transition name="heightChange">
    <div class="header" :class="scrolled ? 'header--scrolled' : ''">
      <div class="header__left">
        <h3 class="header__me">Ryan Bazzana</h3>
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
    height: auto;
    display: block;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    max-width: 100%;
    margin: 0 auto;
    background-color: #e8e8e8;
    border-top: 1px solid #c8c8c8;
    border-bottom: 1px solid #c8c8c8;
    color: #000;
    z-index: 5;
    div {
      vertical-align: middle;
    }
  }
  &__me {
    vertical-align: middle;
    margin: 0px;
  }
  // &__photo {
  //   display: inline-block;
  //   img {
  //     position: relative;
  //     width: 100px;
  //     height: 100px;
  //     border-radius: 50%;
  //     display: inline-block;
  //     margin: 0px;
  //   }
  // }
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
      color: #000;
      transition: all 0.3s ease;
      text-decoration: none;
      &:hover {
        color: #000;
        font-size: 2vw;
        text-decoration: underline;
      }
    }
  }
}
</style>
