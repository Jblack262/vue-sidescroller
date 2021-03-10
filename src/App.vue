<template>
  <div id="app">
    <Navbar @isShowingNav="showingNav" @showingPage1="showPage1" @showingPage2="showPage2" @showingPage3="showPage3" @showingPage4="showPage4"/>
    <div class="outwrapper" id="main">
      <div class="wrapper">
        <Body1 class="slide" :class="{navShown: isNavShown}"/>
        <Body2 class="slide" :class="{navShown: isNavShown}"/>
        <Body3 class="slide" :class="{navShown: isNavShown}"/>
        <Body4 class="slide" :class="{navShown: isNavShown}"/>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Body1 from './components/Body1.vue'
import Body2 from './components/Body2.vue'
import Body3 from './components/Body3.vue'
import Body4 from './components/Body4.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    Body1,
    Body2,
    Body3,
    Body4,
  },
  data() {
    return {
      isNavShown: false,
      showBody1: true,
      showBody2: false,
      showBody3: false,
    }
  },
  methods: {
    showingNav(x) {
      this.isNavShown = x;
    },
    showPage1() {
      document.getElementById('main').scroll({
        top: window.innerWidth,
        behavior: 'smooth'
      });
    },
    showPage2() {
      document.getElementById('main').scroll({
        top: window.innerWidth * 2,
        behavior: 'smooth'
      });
    },
    showPage3() {
      document.getElementById('main').scroll({
        top: window.innerWidth * 3,
        behavior: 'smooth'
      });
    },
    showPage4() {
      document.getElementById('main').scroll({
        top: window.innerWidth * 4,
        behavior: 'smooth'
      });
    },
  }
}
</script>

<style>
html {
  margin: 0;
  padding: 0;
  background: skyblue;
}
.wrapper {
  transform: rotate(90deg) translateY(-100vh);
  transform-origin: top left;
}
.outwrapper {
  width: calc(100vh - 55px);
  height: 100vw;
  transform: rotate(-90deg) translateX(-100vh);
  transform-origin: top left;
  transition: margin 500ms ease;
  overflow-y: scroll;
  overflow-x: hidden;
  position: absolute;
  left: 0;
  top: 0;
}
.navShown {
  transform-origin: top;
  transform: translateY(150px);
}
.slide {
  width: 100vw;
  height: 100vh;
  transition: transform 500ms ease;
}
.wrapper {
  display: flex;
  flex-direction: row;
  width: 400vw;
}
</style>
