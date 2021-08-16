<template>
  <div class="questions-component">
    <div v-if="num==1" class="container def-question-container">
      <div class="question question-1">
        <div class="question-title main-title">
          Боитесь ли вы умереть?
        </div>
        <div class="question-btns">
          <button @click="num++" class="btn questions-btn">Да</button>
          <button @click="num++" class="btn questions-btn">Нет</button>
        </div>
        <div class="question-number">
          Вопрос {{num}}-5
        </div>

        <div class="question-marks">
          <img src="../../../src/images/runes-1.svg" alt="" class="question-runes">
          <div class="question-marks__text">
            Вы, конечно, умрете.
            <p>И все, с кем вы знакомы,</p>
            <p>тоже однажды умрут.</p>
          </div>
          <img src="../../../src/images/runes-2.svg" alt="" class="question-runes">
        </div>
      </div>
      <footer class="footer def-footer">
        TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU DE DIVERTISMENT. PRIN FOLOSIREA LUI DECLARATI CA AVETI 18 ANI IMPLINITI,
      </footer>
    </div>

    <div v-else-if="num==2" class="container questions-container">
      <div class="question question-2">
        <div class="question-marks bottom-line-marks">
          <div class="question-marks__text bottom-line-text">
            Мы расскажем Вам не только подробности вашей смерти, но также поможем Вам избежать этой ужасной даты и продлить вашу жизнь на многие годы.
          </div>
        </div>
        <div class="question-title">
          Когда Вы чувствуете себя наиболее <p>комфортно?</p>
        </div>
        <div class="question-btns">
          <button @click="num++" class="btn questions-btn">Утро</button>
          <button @click="num++" class="btn questions-btn">День</button>
          <button @click="num++" class="btn questions-btn">Вечер</button>
          <button @click="num++" class="btn questions-btn">Ночь</button>
        </div>
        <div class="question-number">
          Вопрос {{num}}-5
        </div>

      </div>
    </div>

    <div v-else-if="num==3" class="container questions-container">
      <div class="question question-3">
        <div class="question-marks bottom-line-marks">
          <div class="question-marks__text bottom-line-text">
            Уже совсем скоро Вы узнаете много интересного о своем будущем!
          </div>
        </div>
        <div class="question-title">
          Укажите свою дату рождения:
        </div>
        <div class="question-btns">
          <select :class="[{error: errorDay}]" class="selection-btn" @change="setDay($event.target.value)">
            <option disabled selected>День</option>
            <option v-for="n in 31" :value="n" :key="n">{{n}}</option>
          </select>
          <select :class="[{error: errorMonth}]" class="selection-btn" @change="setMonth($event.target.value)">
            <option disabled selected>Месяц</option>
            <option v-for="n in 12" :value="n" :key="n">{{n}}</option>
          </select>
          <select :class="[{error: errorYear}]" class="selection-btn" @change="setYear($event.target.value)">
            <option disabled selected>Год</option>
            <option v-for="n in yearArr" :value="n" :key="n">{{n}}</option>
          </select>
          <button @click="validate()" class="btn questions-btn">Далее</button>
        </div>
        <div class="question-number">
          Вопрос {{num}}-5
        </div>
      </div>
    </div>
    <div v-if="loadingCircle" class="container loading-container">
      <div id="floatingCirclesG">
        <div class="f_circleG" id="frotateG_01"></div>
        <div class="f_circleG" id="frotateG_02"></div>
        <div class="f_circleG" id="frotateG_03"></div>
        <div class="f_circleG" id="frotateG_04"></div>
        <div class="f_circleG" id="frotateG_05"></div>
        <div class="f_circleG" id="frotateG_06"></div>
        <div class="f_circleG" id="frotateG_07"></div>
        <div class="f_circleG" id="frotateG_08"></div>
        <div class="f_circleG" id="frotateG_09"></div>
        <div class="f_circleG" id="frotateG_10"></div>
        <div class="f_circleG" id="frotateG_11"></div>
        <div class="f_circleG" id="frotateG_12"></div>
      </div>
      <div class="loading-text">
        Loading...
      </div>
    </div>

    <div v-else-if="num==4" class="container questions-container">
      <div class="question question-4">
        <div class="question-marks bottom-line-marks">
          <div class="question-marks__text bottom-line-text">
            Смерть родного человека – одно из тяжелейших испытаний в жизни каждого из нас!
          </div>
        </div>
        <div class="question-title">
          Снятся ли Вам умершие люди?
        </div>
        <div class="question-btns">
          <button @click="num++" class="btn questions-btn">Да</button>
          <button @click="num++" class="btn questions-btn">Нет</button>
          <button @click="num++" class="btn questions-btn">Иногда</button>
        </div>
        <div class="question-number">
          Вопрос {{num}}-5
        </div>

      </div>
    </div>

    <div v-else-if="num==5" class="container questions-container">
      <div class="question question-5">
        <div class="question-marks bottom-line-marks">
          <div v-if="age <= 35 && age > 18" class="question-marks__text bottom-line-text message-mark">
            По вам скучает очень близкий человек, которого больше нет в мире живых.
          </div>
          <div v-else-if="age <= 45 && age > 36" class="question-marks__text bottom-line-text message-mark">
            По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это дедушка или бабушка.
          </div>
          <div v-else-if="age > 46" class="question-marks__text bottom-line-text message-mark">
            По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это кто-то из Ваших родителей.
          </div>
        </div>
        <div class="question-title">
          Запись, которую Вы услышите, может шокировать людей с неокрепшей психикой. Вы готовы узнать, что ждет именно Вас?
        </div>
        <div class="question-btns">
          <button @click="loadAudio()" class="btn questions-btn">Да</button>
          <button @click="loadAudio()" class="btn questions-btn">Затрудняюсь ответить</button>
        </div>
        <div class="question-number">
          Вопрос {{num}}-5
        </div>

      </div>
    </div>

    <div v-if="loading" class="container loading-container">
      <div class="loading-pic">
        <img src="../../../src/images/mic.svg" alt="" class="mic-img">
      </div>
      <div class="loading-line">
        <div :style="`left : ${percentage}%`" class="load-line"></div>
      </div>
      <div class="percentage">
        {{100+percentage}} %
      </div>
      <div class="loading-text">
        Запись сообщения
      </div>
    </div>

    <div v-else-if="num==6" class="container end-container">
      <div class="question end">
        <div class="end-marks">
          <div class="message-mark last-mark">
            Спасибо за Ваши ответы! <p><span style="font-weight : 700">Мы подготовили для Вас персональную аудио запись с Вашим прогнозом.</span></p>
          </div>
        </div>
        <div class="end-title">
          Вы можете узнать, как повлиять на события, которые ожидают вас в ближайшем будущем.
        </div>
        <div class="end-text">
          <span style="text-transform : uppercase; font-weight : 700">Первое значимое событие может произойти уже</span> <p>{{tomorrow}}, Вам надо быть готовым, что бы последствия не оказались необратимыми.</p>
        </div>
        <div class="end-title">
          Нажмите на кнопку ниже прямо сейчас и наберите наш номер телефона. Прослушайте важную информацию!
        </div>
        <div class="end-btns">
          <button @click="getAudio()" class="btn end-btn">Позвонить и прослушать</button>
        </div>
      </div>
      <footer class="footer">
        TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU DE DIVERTISMENT. PRIN FOLOSIREA LUI DECLARATI CA AVETI 18 ANI IMPLINITI,
      </footer>
    </div>

    <div v-if="info" class="info">
      <div class="info-block">
        <div @click="info = false" class="close-elem">X</div>
        <ul class="info-list">
          <li class="info-item">
            Имя : {{infoObj.name}}
          </li>
          <li class="info-item">
            Пол : {{infoObj.gender}}
          </li>
          <li class="info-item">
            Вес : {{infoObj.mass}}
          </li>
          <li class="info-item">
            Дата рождения : {{infoObj.birth_year}}
          </li>
          <li class="info-item">
            Рост : {{infoObj.height}}
          </li>
          <li class="info-item">
            Цвет глаз : {{infoObj.eye_color}}
          </li>
          <li class="info-item">
            Цвет кожи : {{infoObj.skin_color}}
          </li>
          <li class="info-item">
            Цвет волос : {{infoObj.hair_color}}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'questions',
  data () {
    return {
      day: 0,
      month: 0,
      year: 0,
      num: 1,
      yearArr: [],
      errorDay: false,
      errorMonth: false,
      errorYear: false,
      loadingCircle: false,
      loading: false,
      age: 0,
      percentage: -100,
      tomorrow: '',
      infoObj: {},
      info: false
    }
  },
  created () {
    for (let i = 1940; i < 2020; i++) {
      this.yearArr.push(i)
    }
    let tomorrowDate = new Date()
    tomorrowDate.setDate(tomorrowDate.getDate() + 1)
    let tempDate = tomorrowDate.toJSON().slice(0, 10)
    this.tomorrow = `${tempDate.slice(8, 10)}.${tempDate.slice(5, 7)}.${tempDate.slice(0, 4)}`
  },
  methods: {
    validate (e) {
      if (this.day === 0) {
        this.errorDay = true
      }
      if (this.month === 0) {
        this.errorMonth = true
      }
      if (this.year === 0) {
        this.errorYear = true
      }
      if (this.errorYear === false && this.errorMonth === false && this.errorDay === false) {
        this.num = -this.num
        this.loadingCircle = true
        setTimeout(() => {
          var utc = new Date().toJSON().slice(0, 10)
          if (Number(utc.slice(5, 7)) > this.month) {
            this.age = Number(utc.slice(0, 4)) - this.year
          } else if (Number(utc.slice(5, 7)) < this.month) {
            this.age = Number(utc.slice(0, 4)) - this.year - 1
          } else if (Number(utc.slice(5, 7)) === this.month) {
            if (Number(utc.slice(8, 10)) >= this.day) {
              this.age = Number(utc.slice(0, 4)) - this.year
            } else if (Number(utc.slice(8, 10)) < this.day) {
              this.age = Number(utc.slice(0, 4)) - this.year - 1
            }
          }
          this.num--
          this.loadingCircle = false
          this.num = -this.num
        }, 2000)
      }
    },
    setDay (e) {
      this.day = e
      this.errorDay = false
    },
    setMonth (e) {
      this.month = e
      this.errorMonth = false
    },
    setYear (e) {
      this.year = e
      this.errorYear = false
    },
    async loadAudio () {
      this.num = -this.num
      this.loading = true
      let timer = setInterval(() => {
        this.percentage++
      }, 30)
      setTimeout(() => {
        clearInterval(timer)
        this.num--
        this.loading = false
        this.num = -this.num
        this.percentage = -100
      }, 3000)
    },
    async getAudio () {
      let response = await fetch('https://swapi.dev/api/people/1/')
      let result = await response.json()
      this.infoObj = result
      this.info = true
    }
  }
}
</script>

<style scoped src="../../components/questions/questions.css">
</style>
