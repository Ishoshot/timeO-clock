<template>
  <div id="app">
    <ion-app>
      <ion-vue-router/>
    </ion-app>
  </div>
</template>

<style>
#app {
/*  font-family: 'Avenir', Helvetica, Arial, sans-serif;*/
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /*color: #2c3e50;*/
}
@import url(https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css);
@import url('https://fonts.googleapis.com/css?family=Muli&display=swap');
@import url('https://fonts.googleapis.com/css?family=Big+Shoulders+Text&display=swap');
@import url('https://fonts.googleapis.com/css?family=Heebo:300&display=swap');

* {
  box-sizing: border-box;
}

:root {
  --primary-color: #000;
  --secondary-color: #fff;
  --primary-color-dark: #fff;
  --secondary-color-dark: #333;
}

html {
  transition: all 0.5s ease-in;
  overflow-y: scroll;
}

body {
  font-family: 'Heebo', sans-serif;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

html.dark {
  --primary-color: var(--primary-color-dark);
  --secondary-color: var(--secondary-color-dark);
}

html.dark {
  background-color: #111;
  color: var(--primary-color);
}

.toggle {
  background-color: var(--primary-color);
  border: 0;
  border-radius: 2px;
  color: var(--secondary-color);
  font-family: 20px;
  padding: 8px 12px;
}

.toggle:focus {
  outline: 0;
}

.goto{
  margin-top:40px;
}

.clock-container {
  display: flex;
  margin-top: 50px;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}

.clock {
  position: relative;
  width: 220px;
  height: 220px;
  margin-bottom:20px;
  border:2px solid #000;
  border-radius: 50%;
}

.needle {
  background-color: var(--primary-color);
  transition: all 0.5s ease-in;
  position: absolute;
  left: 50%;
  top: 50%;
  transform-origin: bottom center;
  width: 3px;
  height: 65px;
}

.digital{
  margin-top:50px;
}

.needle.hour {
  background-color: #e89c0c;
  transform: translate(-50%, -100%) rotate(0deg);
}

.needle.minute {
  background-color: #e74c3c;
  transform: translate(-50%, -100%) rotate(0deg);
  height: 100px;
}

.needle.second {
  background-color: #000;
  height: 100px;
  transform: translate(-50%, -100%) rotate(0deg);
}

.center-point {
  background-color: #e74c3c;
  border-radius: 50%;
  width: 10px;
  height: 10px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.center-point::after {
  background-color: var(--primary-color);
  transition: all 0.5s ease-in;
  border-radius: 50%;
  content: '';
  width: 5px;
  height: 5px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.time {
  font-size: 60px;
}

.date {
  color: #aaa;
  font-size: 14px;
  letter-spacing: 0.3px;
  text-transform: uppercase;
}

.date .circle {
  background-color: var(--primary-color);
  border-radius: 50%;
  color: var(--secondary-color);
  display: inline-flex;
  padding: 15px;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  line-height: 18px;
  transition: all 0.5s ease-in;
  width: 18px;
  height: 18px;
}
</style>
