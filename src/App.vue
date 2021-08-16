<template>
  <div id="app">
    <section class="section welcome-section">
      <welcome/>
    </section>

    <section class="section desc-section">
      <mainDesk/>
    </section>

    <section class="section questions-section">
      <questions/>
    </section>
  </div>
</template>

<script>
import welcome from './components/welcome/welcome'
import mainDesk from './components/mainDesk/mainDesk'
import questions from './components/questions/questions'

export default {
  name: 'App',
  components: {
    welcome,
    mainDesk,
    questions
  },
  data () {
    return {
      scrolled: false
    }
  },
  created () {
    window.addEventListener('scroll', this.handleScroll)
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll (event) {
      if (this.scrolled === false) {
        if (self.pageYOffset > window.screen.height * 0.3) {
          this.scrolled = true
          document.querySelector('.desc-section').style.opacity = 1
        }
      }
    }
  }
}
</script>

<style src="../src/styles/base.css">
</style>
