<template>
  <div id="app">
    <header class="header">
      <h1 class="header__title">Лучшие астрологи и экстрасенсы Румынии</h1>
    </header>

    <hr />

    <div class="main-container">
      <section class="greeting">
        <p class="greeting__text">Точность прогноза: 97%</p>
        <div class="container-img">
          <img
            class="greeting__img"
            src="./assets/woman-icon.png"
            alt="Девушка"
          />
        </div>
        <h2 class="greeting__title">
          Вас беспокоит вопрос о том,<br />
          <span class="greeting__title_uppercase"
            >когда Вы покинете этот Мир и при каких обстоятельствах?
          </span>
        </h2>

        <div class="button__container">
          <button class="button">Да</button>
          <button class="button">Нет</button>
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
      </section>
    </div>

    <section class="addition">
      <div class="addition__text-container">
        <p class="addition__text">
          Многие не верят предсказаниям и мы решили доказать каждому, <br />
          <span class="addition__text_accent"
            >что прогноз может изменить жизнь любого человека!</span
          >
        </p>
      </div>
    </section>

    <div class="questions__wrapper">
      <div class="main-container">
        <section class="questions">
          <h2 class="questions__title">Боитесь ли вы умереть?</h2>
          <div class="button__container button__container_small-mt">
            <button class="button">Да</button>
            <button class="button">Нет</button>
            <span class="button__subtext questions__number">Вопрос 1-5</span>
          </div>
          <div class="questions__statement">
            <img
              class="questions__statement-img"
              src="./assets/rune1.svg"
              alt="Руна"
            />
            <p class="questions__statement-text">
              Вы, конечно, умрете. <br />
              И все, с кем вы знакомы, <br />тоже однажды умрут.
            </p>
            <img
              class="questions__statement-img"
              src="./assets/rune2.svg"
              alt="Руна"
            />
          </div>
        </section>
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
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      questions: [
        {
          title: "Боитесь ли вы умереть?",
          answerFirst: "Да",
          answerSecond: "Нет",
          statement: `Вы, конечно, умрете. <br />
              И все, с кем вы знакомы, <br />тоже однажды умрут.`,
        },
      ],
    }
  },
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Bad+Script&family=Roboto:wght@300;400&display=swap");
@import "./_variabels.css";
@import "./_animation.css";

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
  opacity: 0.9;
  background: no-repeat center / 100% url(assets/bg_blik.png);
  top: -75%;
  left: 50%;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
  transform: translate(-50%);
}
.header {
  height: 75px;
  display: flex;
  justify-content: center;
  align-items: center;
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
hr {
  border-color: var(--main-color);
}
.main-container {
  position: relative;
  width: 443px;
}
.greeting {
  margin-top: 7px;
}
.greeting__text {
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
.greeting__title {
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

  /* background: linear-gradient(
    248.67deg,
    rgba(255, 255, 255, 0) 30.84%,
    rgba(255, 255, 255, 0.29) 46.06%,
    rgba(255, 255, 255, 0) 64.04%
  ); rgba(246, 200, 102, 0.9) -6.2%,*/
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
.questions__wrapper {
  position: relative;
  max-width: 1440px;
}
.questions {
  margin-top: 129px;
  margin-bottom: 153px;
}
.questions__title {
  color: var(--accent-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  text-transform: uppercase;
}
.button__container_small-mt {
  margin-top: 14px;
}
.questions__statement {
  margin-top: 116px;
}
.questions__statement-text {
  font-family: var(--accent-font);
  color: var(--additional-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
}
.questions__statement-img {
  height: 17px;
}
.questions__statement-img:first-child {
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
</style>
