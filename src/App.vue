<template>
  <div id="app">
    <section id="greeting" class="greeting">
      <header class="header">
        <h1 class="header__title">Лучшие астрологи и экстрасенсы Румынии</h1>
      </header>

      <div class="main-container">
        <p class="greeting__text">Точность прогноза: 97%</p>
        <div class="container-img">
          <img
            class="greeting__img"
            src="./assets/woman-icon.png"
            alt="Девушка"
          />
        </div>
        <h2 class="title greeting__title">
          Вас беспокоит вопрос о том,<br />
          <span class="greeting__title_uppercase"
            >когда Вы покинете этот Мир и при каких обстоятельствах?
          </span>
        </h2>

        <div class="button__container">
          <a class="button button-link" href="#questions">Да</a>
          <a class="button button-link" href="#addition">Нет</a>
          <span class="button__subtext">Онлайн предсказание</span>
        </div>

        <div class="invitation__container">
          <div class="container-img">
            <img class="invitation__img" src="./assets/hands.png" alt="" />
          </div>
          <p class="invitation__text">
            Позвольте нам раскрыть эту волнующую тайну и <br />
            <span class="invitation__text_accent"
              >с точностью определить дату и время вашей смерти,</span
            >
            а также предшествующую этому событию причину
          </p>
        </div>
      </div>
    </section>

    <section id="addition" class="addition">
      <div class="addition__text-container">
        <p class="addition__text">
          Многие не верят предсказаниям и мы решили доказать каждому, <br />
          <span class="addition__text_accent"
            >что прогноз может изменить жизнь любого человека!</span
          >
        </p>
      </div>
    </section>

    <section
      id="questions"
      v-if="this.currentQuestion + 1 < this.questions.length"
      class="questions"
    >
      <div v-if="this.currentQuestion === 0" class="questions__wrapper">
        <div class="main-container">
          <h2 class="questions__title">
            {{ this.questions[this.currentQuestion].title }}
          </h2>
          <div class="button__container button__container_small-mt">
            <button
              class="button"
              @click="turnToNextQuestion"
              v-for="option of questions[this.currentQuestion].answersOptions"
              :key="option"
            >
              {{ option }}
            </button>
            <span class="button__subtext questions__number"
              >Вопрос {{ this.questions[this.currentQuestion].id }}-{{
                this.questions.length
              }}
            </span>
          </div>
          <div class="questions__statement">
            <img
              class="questions__statement-img"
              src="./assets/rune1.svg"
              alt="Руна"
            />
            <p class="questions__statement-text">
              {{ this.questions[this.currentQuestion].statement[0] }}
            </p>
            <img
              class="questions__statement-img"
              src="./assets/rune2.svg"
              alt="Руна"
            />
          </div>
        </div>
        <img
          class="questions__img-bg moon-img"
          src="./assets/moon.svg"
          alt="Луна"
        />
        <img
          class="questions__img-bg eye-img"
          src="./assets/eye.svg"
          alt="Глаз"
        />
      </div>
      <div
        v-else-if="
          this.currentQuestion !== 0 &&
          this.currentQuestion + 1 <= this.questions.length
        "
      >
        <div class="questions__statement questions__statement-header">
          <p class="questions__statement-text questions__statement-text-header">
            {{ this.questions[this.currentQuestion].statement[0] }}
          </p>
        </div>

        <div class="main-container">
          <h2 class="questions__title">
            {{ this.questions[this.currentQuestion].title }}
          </h2>
          <div
            v-show="this.questions[this.currentQuestion].isDatepicker"
            class="datepicker__container"
          >
            <div class="input__container">
              <input
                class="input"
                type="text"
                ref="datepicker"
                placeholder="Дата рождения"
              />
            </div>
          </div>
          <div class="button__container button__container_small-mt">
            <button
              class="button"
              @click="turnToNextQuestion"
              v-for="option of questions[this.currentQuestion].answersOptions"
              :key="option"
            >
              {{ option }}
            </button>
          </div>
          <span class="button__subtext questions__number"
            >Вопрос {{ this.questions[this.currentQuestion].id }}-{{
              this.questions.length
            }}</span
          >
        </div>
        <div class="questions__wrapper">
          <img
            class="questions__img-bg moon-img"
            src="./assets/moon.svg"
            alt="Луна"
          />
          <img
            class="questions__img-bg eye-img"
            src="./assets/eye.svg"
            alt="Глаз"
          />
        </div>
      </div>
    </section>
    <section
      class="result"
      v-if="this.currentQuestion + 1 >= this.questions.length"
    >
      <div class="main-container">
        <h2 class="title title__result">
          Спасибо за Ваши ответы! Мы подготовили для Вас персональную аудио
          запись с Вашим прогнозом.
        </h2>
        <div class="result__container">
          <p class="result__text result__text_accent">
            Первое значимое событие может произойти уже
            {{ tomorrowDay }},
            <span class="result__text"
              >вам надо быть готовым, что бы последствия не оказались
              необратимыми.
            </span>
          </p>
        </div>
        <p class="result__subtext">
          Нажмите на кнопку ниже прямо сейчас и наберите наш номер телефона.
          Прослушайте важную информацию!
        </p>
        <div class="button__container">
          <a
            href="#greeting"
            @click="resetResult"
            class="button button-link button_accent"
            >Позвонить и прослушать</a
          >
        </div>
      </div>
      <p class="result__footer">
        TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU DE DIVERTISMENT. PRIN
        FOLOSIREA LUI DECLARATI CA AVETI 18 ANI IMPLINITI,
      </p>
    </section>
  </div>
</template>

<script>
//v-if="this.currentQuestion + 1 > this.questions.length"
export default {
  name: "App",
  data() {
    return {
      tomorrowDay: null,
      currentQuestion: 0,
      questions: [
        {
          id: 1,
          title: "Боитесь ли вы умереть?",
          answersOptions: ["Да", "Нет"],
          statement: [
            "Вы, конечно, умрете. И все, с кем вы знакомы, тоже однажды умрут.",
          ],
        },
        {
          id: 2,
          title: "Когда Вы чувствуете себя наиболее комфортно?",
          answersOptions: ["Утро", "День", "Вечер", "Ночь"],
          statement: [
            "Мы расскажем Вам не только подробности вашей смерти, но также поможем Вам избежать этой ужасной даты и продлить вашу жизнь на многие годы.",
          ],
        },
        {
          id: 3,
          title: "Укажите свою дату рождения:",
          answersOptions: ["Далее"],
          statement: [
            "Уже совсем скоро Вы узнаете много интересного о своем будущем!",
          ],
          isDatepicker: true,
        },
        {
          id: 4,
          title: "Снятся ли Вам умершие люди?",
          answersOptions: ["Да", "Нет", "Иногда"],
          statement: [
            "Смерть родного человека – одно из тяжелейших испытаний в жизни каждого из нас!",
          ],
        },
        {
          id: 5,
          title:
            "Запись, которую Вы услышите, может шокировать людей с неокрепшей психикой. Вы готовы узнать, что ждет именно Вас?",
          answersOptions: ["Да", "Затрудняюсь ответить"],
          statement: [
            "По вам скучает очень близкий человек, которого больше нет в мире живых.",
            "По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это дедушка или бабушка.",
            "По вам скучает очень близкий человек, которого больше нет в мире живых. Возможно это кто-то из Ваших родителей.",
          ],
        },
      ],
      answers: [
        {
          dateOfBirth: null,
        },
      ],
    }
  },
  mounted() {
    this.setTomorrow()
  },
  beforeUpdate() {
    let currentYear = new Date().getFullYear()
    this.date = window.M.Datepicker.init(this.$refs.datepicker, {
      format: "dd.mm.yyyy",
      yearRange: [1920, currentYear],
      i18n: {
        cancel: "Отмена",
        clear: "Очистить",
        weekdays: [
          "Воскресенье",
          "Понедельник",
          "Вторник",
          "Среда",
          "Четверг",
          "Пятница",
          "Суббота",
        ],
        weekdaysShort: ["Вс", "Пн", "Вт", "Ср", "Чт", "Пт", "Сб"],
        weekdaysAbbrev: ["Вс", "Пн", "Вт", "Ср", "Чт", "Пт", "Сб"],
        months: [
          "Январь",
          "Февраль",
          "Март",
          "Апрель",
          "Май",
          "Июнь",
          "Июль",
          "Август",
          "Сентябрь",
          "Октябрь",
          "Ноябрь",
          "Декабрь",
        ],
      },
      monthsShort: [
        "Янв",
        "Фев",
        "Мар",
        "Апр",
        "Май",
        "Июн",
        "Июл",
        "Авг",
        "Сен",
        "Окт",
        "Ноя",
        "Дек",
      ],
    })
  },
  methods: {
    resetResult() {
      this.currentQuestion = 0
    },
    turnToNextQuestion() {
      this.currentQuestion++
      console.log(this.currentQuestion)
    },
    setTomorrow() {
      let today = new Date()
      let tomorrow = new Date(today.getTime() + 24 * 60 * 60 * 1000)
      let dayTomorrow =
        tomorrow.getDate() > 10 ? tomorrow.getDate() : `0` + tomorrow.getDate()
      let monthTomorrow = tomorrow.getMonth() + 1
      let yearTomorrow = tomorrow.getFullYear()
      this.tomorrowDay = `${dayTomorrow}.${monthTomorrow}.${yearTomorrow}`
    },
  },
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Bad+Script&family=Roboto:wght@300;400&display=swap");
@import "./_variabels.css";
@import "./_animation.css";
@import "~materialize-css/dist/css/materialize.min.css";

* {
  box-sizing: border-box;
  margin: 0 auto;
  padding: 0;
}
body {
  position: relative;
  z-index: -100;
  height: 100%;
  background-color: #202024;
}
#app {
  position: relative;
  font-family: Roboto, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  z-index: -5;
  overflow: hidden;
}
#app::before {
  content: "";
  width: 100%;
  height: 1090px;
  position: absolute;
  background: no-repeat center / 120vw url(assets/bg_blik.png);
  background-position: top;
  z-index: -1;
  transform: translate(-50%);
  opacity: 0.9;
}
.input__container {
  position: relative;
  height: 200px;
}
.datepicker-date-display {
  display: none;
}
.header {
  height: 75px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-bottom: 1px solid var(--main-color);
}
.header__title {
  margin-top: 19px;
  color: var(--main-color);
  font-size: var(--small-font-size);
  line-height: var(--small-line-height);
  font-weight: var(--small-font-weight);
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  -webkit-text-stroke: 0.5px rgb(0, 0, 0);
  letter-spacing: var(--small-letter-spacing);
}
.main-container {
  position: relative;
  width: 443px;
}
.greeting__text {
  margin-top: 7px;
  color: var(--main-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  letter-spacing: var(--normal-letter-spacing);
}
.greeting__img {
  margin-top: 40px;
  width: 390px;
  height: 100%;
}
.title {
  color: var(--accent-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  letter-spacing: var(--negative-letter-spacing);
}
.greeting__title_uppercase {
  text-transform: uppercase;
}
.button__container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 30px;
}
.button {
  position: relative;
  height: var(--button-height);
  width: var(--button-width);
  margin-top: 34px;
  border-radius: var(--button-border-radius);
  border: none;
  cursor: pointer;
  color: var(--additional-color);
  font-size: var(--button-font-size);
  line-height: var(--button-line-height);
  font-weight: var(--normal-font-weight);
  background: var(--button-main-gradient);
  overflow: hidden;
}
.button-link {
  text-decoration: none;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.button::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 5em;
  height: 100%;
  background: var(--button-glint-gradient);
  transform: translateX(-10em) skewX(45deg);
  animation: move-light 1.5s infinite linear;
}
.button__subtext {
  display: inline-block;
  margin-top: 36px;
  color: var(--main-color);
  font-size: var(--small-font-size);
  line-height: var(--small-line-height);
  font-weight: var(--small-font-weight);
  letter-spacing: var(--small-letter-spacing);
}
.invitation__container {
  position: relative;
  display: inline-block;
  margin-top: 143px;
  padding: 128px 37px 102px 37px;
  border: var(--main-color) 1px solid;
}
.invitation__img {
  position: absolute;
  margin-top: 42px;
  width: 135px;
  height: 135px;
  top: -10%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.invitation__text {
  color: var(--additional-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  letter-spacing: var(--additiona-letter-spacing);
}
.invitation__text_accent {
  color: var(--accent-color) !important;
}
.addition {
  max-width: 1440px;
  position: relative;
  height: 606px;
  margin-top: 69px;
  padding-top: 241px;
}
.addition::before {
  content: "";
  width: 100%;
  background-color: #3d3e42;
  background: no-repeat center / cover url(assets/image7.jpg);
  top: 0;
  left: 50%;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
  opacity: 0.2;
  transform: translate(-50%);
}
.addition__text-container {
  width: 443px;
  padding-left: 37px;
  padding-right: 37px;
}
.addition__text {
  color: var(--additional-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
}
.addition__text_accent {
  color: var(--accent-color) !important;
}
.questions {
  min-height: 1010px;
}
.questions__wrapper {
  position: relative;
  max-width: 1440px;
  margin-bottom: 153px;
}
.questions__title {
  margin-top: 100px;
  color: var(--accent-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  text-transform: uppercase;
}
.button__container_small-mt {
  margin-top: 14px;
}
.questions__statement-header {
  height: 224px;
  display: flex;
  align-items: center;
  border-bottom: 1px solid var(--main-color);
}
.questions__statement-text {
  max-width: 222px;
  font-family: var(--accent-font);
  color: var(--additional-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
}
.questions__statement-text-header {
  max-width: 415px;
}
.questions__statement-img {
  height: 17px;
}
.questions__statement-img:first-child {
  margin-top: 116px;
  margin-bottom: 77px;
}
.questions__statement-img:last-child {
  margin-top: 84px;
}
.questions__img-bg {
  position: absolute;
  z-index: 2;
  opacity: 0.2;
}
.moon-img {
  height: 164px;
  left: -3%;
  bottom: -13.7%;
}
.eye-img {
  height: 204px;
  right: -9%;
  bottom: 28.2%;
}
.input__container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: var(--button-height);
  width: var(--button-width);
  margin-top: 34px;
  border-radius: var(--button-border-radius);
  border: none;
  background: var(--select-main-gradient);
  box-shadow: var(--select-shadow);
  cursor: pointer !important;
}
.datepicker__container {
  position: relative;
}
.input {
  text-align: center;
  font-size: var(--button-font-size) !important;
  line-height: var(--button-line-height) !important;
  font-weight: var(--normal-font-weight) !important;
  color: var(--select-color) !important;
  border: none !important;
  cursor: pointer !important;
}
input[type="text"]:not(.browser-default):focus:not([readonly]) {
  border: none !important;
  box-shadow: none !important;
}
.input::placeholder {
  text-align: center;
  font-size: var(--button-font-size);
  line-height: var(--button-line-height);
  font-weight: var(--normal-font-weight);
  color: var(--select-color) !important;
}
.btn-flat,
.is-today {
  color: var(--date-accent-color) !important;
}
.is-selected {
  background-color: var(--date-accent-color) !important;
  color: white !important;
}
.month-prev:focus,
.month-next:focus {
  background-color: var(--date-accent-color) !important;
}
.dropdown-content li > a,
.dropdown-content li > span {
  color: var(--date-accent-color) !important;
}
.datepicker-modal {
  top: 25% !important;
}
.dropdown-content {
  top: 2590px !important;
  height: 350px;
}
.result {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 1000px;
  padding: 50px;
}
.title__result {
  color: var(--additional-color);
}
.result__container {
  position: relative;
  display: inline-block;
  margin-top: 40px;
  padding: 50px;
  border: var(--main-color) 1px solid;
}
.button_accent {
  background: var(--button-accent-gradient);
}

.result__text {
  color: var(--accent-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  letter-spacing: var(--additiona-letter-spacing);
}
.result__text_accent {
  font-weight: var(--bold-font-weight);
}
.result__subtext {
  margin-top: 50px;
  color: var(--additional-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  letter-spacing: var(--negative-letter-spacing);
}
.result__footer {
  color: var(--main-color);
  font-size: var(--small-font-size);
  line-height: var(--small-line-height);
  font-weight: var(--small-font-weight);
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  -webkit-text-stroke: 0.5px rgb(0, 0, 0);
  letter-spacing: var(--small-letter-spacing);
}
</style>
