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
          <img class="greeting__img" src="./assets/woman-icon.png" alt="" />
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
        </div>
        <span class="greeting__subtext">Онлайн предсказание</span>
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
      <section class="addition">
        <p class="addition__text">
          Многие не верят предсказаниям и мы решили доказать каждому, <br />
          <span class="addition__text_accent"
            >что прогноз может изменить жизнь любого человека!</span
          >
        </p>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
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
#app {
  font-family: Roboto, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #202024;
  height: 100%;
}
.header {
  height: 75px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header__title {
  color: var(--main-color);
  font-size: var(--small-font-size);
  line-height: var(--small-line-height);
  font-weight: var(--small-font-weight);
  text-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  -webkit-text-stroke: 0.3px rgb(0, 0, 0);
}
hr {
  border-color: var(--main-color);
}
.main-container {
  width: 443px;
  margin-top: 12px;
}
.greeting__text {
  color: var(--main-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
}
.greeting__img {
  margin-top: 42px;
  width: 390px;
  height: 100%;
}
.greeting__title {
  color: var(--accent-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
}
.greeting__title_uppercase {
  text-transform: uppercase;
}
.button__container {
  margin-top: 74px;
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
.button:before {
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
.greeting__subtext {
  display: inline-block;
  margin-top: 35px;
  color: var(--main-color);
  font-size: var(--small-font-size);
  line-height: var(--small-line-height);
  font-weight: var(--small-font-weight);
}
.invitation__container {
  position: relative;
  display: inline-block;
  margin-top: 146px;
  padding: 128px 37px 84px 37px;
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
}
.invitation__text_accent {
  color: var(--accent-color) !important;
}
.addition {
  display: flex;
  align-items: center;
  height: 606px;
  margin-top: 69px;
  background: rgb(82, 79, 102);
}
.addition__text {
  color: var(--additional-color);
  font-size: var(--normal-font-size);
  line-height: var(--normal-line-height);
  font-weight: var(--normal-font-weight);
  opacity: none !important;
}
.addition__text_accent {
  color: var(--accent-color) !important;
}
</style>
