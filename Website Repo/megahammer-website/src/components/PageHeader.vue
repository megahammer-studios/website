<template>
  <div class="header">

    <div class="header-bg"
    :style="{ opacity: scroll/64 }">
    </div>

      <div class="header-content"
      :style="{ padding: changingPadding + 'px'}">

      <img src="../assets/just_text.png" class="logo"
      :style="{ height: changingHeight + 'px'}">



      </div>
  </div>
</template>

<script>
export default {
  name: "PageHeader",
  data: function () {
    return {
      scroll: 0,
      changingPadding: 0,
      changingHeight: 0
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll);

    this.handleScroll();
  },
  unmounted () {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll () {
      this.scroll = window.scrollY;

      this.changingPadding = Math.max(64 - this.scroll/2, 8);

      this.changingHeight = Math.max(Math.min(100-this.scroll/2, 80), 60);
    }
  }
}
</script>

<style scoped>
.header {

  width: 100%;

  display: flex;
  align-items: center;
  justify-content: center;

  position: fixed;

  z-index: 1000;

}

.header-content {
  padding: 32px;
}

.header-bg {

  width: 100%;
  height: 100%;

  background-color: #050505;

  position: absolute;
  z-index: -100;

  box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.3);
}

.logo {

  image-rendering: crisp-edges;

}

@media only screen and (max-width: 600px) {
  .logo {
    max-height: 60px;
  }
}
</style>