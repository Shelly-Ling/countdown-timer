<template>
  <div class="timmer">
    <h1>Countdown Clock</h1>
    <div id="clockdiv">
      <div class="time-card">
        <span class="days"></span>
        <div class="text">Days</div>
      </div>
      <div class="time-card">
        <span class="hours"></span>
        <div class="text">Hours</div>
      </div>
      <div class="time-card">
        <span class="minutes"></span>
        <div class="text">Minutes</div>
      </div>
      <div class="time-card">
        <span class="seconds"></span>
        <div class="text">Seconds</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
body {
  text-align: center;
  background: #00ecb9;
  font-family: sans-serif;
  font-weight: 100;
}
.timmer {
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.time-card {
  width: 150px;
  height: 200px;
  margin: 15px;
}
h1 {
  color: #396;
  font-weight: 400;
  font-size: 40px;
  margin: 40px 0px 20px;
  text-align: center;
}
#clockdiv {
  font-family: sans-serif;
  color: #fff;
  display: inline-block;
  font-weight: 100;
  text-align: center;
  font-size: 30px;
}
#clockdiv > div {
  padding: 10px;
  border-radius: 5px;
  background: #00bf96;
  display: inline-block;
}
#clockdiv div > span {
  width: 90%;
  height: 80%;
  border-radius: 5px;
  background: #00816a;
  display: inline-block;
}
.text {
  font-size: 30px;
}
</style>