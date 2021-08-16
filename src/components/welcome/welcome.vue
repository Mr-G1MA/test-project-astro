<template>
  <div class="welcome-component">
    <div class="container welcome-container">
      <header class="header">
        <div class="header__title">
          Лучшие астрологи и экстрасенсы Румынии
        </div>
      </header>
      <div class="welcome__question-wrapper">
        <div class="welcome__question">
          <div class="welcome__question-title">
            Точность прогноза: 97%
          </div>
          <form class="welcome__question-form">
            <div class="welcome__question-pic">
              <img src="../../../src/images/woman1.png" alt="woman" class="welcome__question-img">
            </div>
            <div class="welcome__question-text">
              Вас беспокоит вопрос о том, КОГДА ВЫ ПОКИНЕТЕ ЭТОТ МИР И ПРИ КАКИХ ОБСТОЯТЕЛЬСТВАХ?
            </div>
            <div class="welcome__question-btns">
              <button class="btn welcome-btn">Да</button>
              <button class="btn">Нет</button>
            </div>
          </form>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'welcome',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style src="../../components/welcome/welcome.css">
</style>
