<template>
  <div class="header" :class="scrolled ? 'header--scrolled' : ''">
    <div class="header__left">
      <h1>Ryan Bazzana</h1>
    </div>
    <div class="header__right">
      <ul>
        <li>
          <a href="#about">About me</a>
        </li>
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
  display: block;
  position: relative;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  background: #75a68e;
  height: 125px;

  &__left {
    position: relative;
    height: 100%;
    display: inline-block;
    width: 40%;
  }
  &__right {
    position: relative;
    height: 100%;
    display: inline-block;
    width: 60%;
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      display: inline-block;
      margin: 0 10px;
    }
    a {
      color: #000;
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
</style>
