<template>
  <div class="timmer">
    <h1>Countdown Clock</h1>
    <div id="clockdiv">
      <div class="time-card">
        <div class="days time">
          <span>{{ days }}</span>
        </div>
        <div class="text">Days</div>
      </div>
      <div class="time-card">
        <div class="hours time">
          <span>{{ hours }}</span>
        </div>
        <div class="text">Hours</div>
      </div>
      <div class="time-card">
        <div class="minutes time">
          <span>{{ minutes }}</span>
        </div>
        <div class="text">Minutes</div>
      </div>
      <div class="time-card">
        <div class="seconds time">
          <span>{{ seconds }}</span>
        </div>
        <div class="text">Seconds</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      endtime: {},
      seconds: -1,
      minutes: -1,
      hours: -1,
      days: -1,
    }
  },
  created() {
    this.getDeadLine()
  },
  mounted() {
    this.getTimeRemaining(this.endtime)
    this.updateClock()
  },
  methods: {
    getDeadLine() {
      this.endtime = new Date(Date.parse(new Date()) + 3 * 24 * 60 * 60 * 1000)
    },
    getTimeRemaining(endtime) {
      const total = Date.parse(endtime) - Date.parse(new Date())
      const seconds = Math.floor((total / 1000) % 60)
      const minutes = Math.floor((total / 1000 / 60) % 60)
      const hours = Math.floor((total / (1000 * 60 * 60)) % 24)
      const days = Math.floor(total / (1000 * 60 * 60 * 24))
      return {
        total,
        days,
        hours,
        minutes,
        seconds
      }
    },
    updateClock() {
      const t = this.getTimeRemaining(this.endtime);

      this.days = ('0' + t.days)
      this.hours = ('0' + t.hours).slice(-2)
      this.minutes = ('0' + t.minutes).slice(-2)
      this.seconds = ('0' + t.seconds).slice(-2)

      if (t.total <= 0) {
        clearInterval(timeinterval)
      }

      const timeinterval = setInterval(this.updateClock, 1000);
      this.deadline = new Date(Date.parse(new Date()) + 3 * 24 * 60 * 60 * 1000);

    },
    initializeClock() {
      this.initializeClock('clockdiv', this.deadline);
    }
  }
}
</script>>

<style scoped>
/* X-Small devices (portrait phones, less than 576px) */

.timmer {
  width: 100vw;
  height: 82vh;
  min-width: 310px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  white-space: nowrap;
}

.time-card {
  display: inline-block;
  width: 20%;
  height: 100px;
  margin: 3px;
  text-align: center;
}
.time {
  width: 101%;
  height: 82%;
  background-color: #50a685;
  border-radius: 5px;
}
#clockdiv div > span {
  border-radius: 5px;
  background-color: #50a685;
  display: inline-block;
  text-align: center;
  font-size: 45px;
  width: auto;
  height: 98%;
  line-height: 82px;
}
.text {
  font-size: 10px;
}
h1 {
  color: #396;
  font-weight: 400;
  font-size: 35px;
  margin: 40px 0px 20px;
  text-align: center;
  min-width: 310px;
}
#clockdiv > div {
  padding: 5px;
  border-radius: 5px;
  background: #595757;
  display: inline-block;
}

#clockdiv {
  font-family: sans-serif;
  color: #fff;
  display: inline-block;
  font-weight: 100;
  text-align: center;
  font-size: 30px;
}
.text {
  font-size: 16px;
}

@media (min-width: 400px) {
  .time-card {
    height: 125px;
  }
  #clockdiv div > span {
    height: 98%;
    font-size: 60px;
    line-height: 105px;
  }
  .text {
    font-size: 20px;
  }
  h1 {
    font-size: 40px;
  }
}

@media (min-width: 576px) {
  .time-card {
    display: inline-block;
    width: 18%;
    height: 150px;
    margin: 3px;
  }
  #clockdiv div > span {
    font-size: 80px;
    width: auto;
    height: 98%;
    line-height: 125px;
  }
  .text {
    font-size: 24px;
  }
  h1 {
    font-size: 45px;
  }
}

/* Small devices (landscape phones, less than 768px) */
@media (min-width: 768px) {
  .time-card {
    width: 20%;
    height: 200px;
    margin: 15px;
    max-width: 170px;
  }

  #clockdiv div > span {
    font-size: 110px;
    width: auto;
    height: 98%;
    line-height: 170px;
  }
  .time {
    width: 101%;
    height: 82%;
    background-color: #50a685;
    border-radius: 5px;
    max-width: 170px;
  }
  .text {
    font-size: 30px;
  }
  h1 {
    font-size: 55px;
  }
}
</style>