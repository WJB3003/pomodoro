<template>
  <div class="timer">
    <div class="sections">
      <button @click="pomodoroTime">Pomodoro</button>
      <button @click="shortBreakTime">Short Break</button>
      <button @click="longBreakTime">Long Break</button>
    </div>
    <h1 class="time">{{minutes}} : {{seconds}}</h1>
    <h2 @click="start" class="start">START</h2>
    <h2 @click="stop" class="stop">STOP</h2>
  </div>
</template>

<script>
export default {
  name: "Timer",
  data() {
    return {
      timerId: "",
      timer: 1500,
      duration: 1500,
      minutes: 25,
      seconds: 0,
      isRunning: false
    };
  },
  methods: {
    pomodoroTime: function() {
        this.stop();
      this.minutes = 25;
      this.seconds = 0;
      this.setTimer();
    },
    shortBreakTime: function() {
        this.stop();
      this.minutes = 2;
      this.seconds = 0;
      this.setTimer();
    },
    longBreakTime: function() {
        this.stop();
      this.minutes = 5;
      this.seconds = 0;
      this.setTimer();
    },
    start: function() {
      this.isRunning = true;
      this.timerCalc(this.timer);
    },
    timerCalc: function(duration) {
      this.timer = duration;
      this.duration = duration;
      var _this = this;
      this.timerId = setInterval(function() {
        _this.minutes = parseInt(_this.timer / 60, 10);
        _this.seconds = parseInt(_this.timer % 60, 10);

        _this.minutes =
          _this.minutes < 10 ? "0" + _this.minutes : _this.minutes;
        _this.seconds =
          _this.seconds < 10 ? "0" + _this.seconds : _this.seconds;

        if (--_this.timer < 0) {
          _this.timer = _this.duration;
          _this.reset();
        }
      }, 1000);
    },
    stop: function() {
      this.isRunning = false;
      return clearInterval(this.timerId);
    },
    setTimer() {
      this.minutes = this.minutes < 10 ? "0" + this.minutes : this.minutes;
      this.seconds = this.seconds < 10 ? "0" + this.seconds : this.seconds;
      this.timer = this.minutes * 60;
      this.duration = this.timer;
    },
  },
  created: function() {
    this.minutes = this.minutes < 10 ? "0" + this.minutes : this.minutes;
    this.seconds = this.seconds < 10 ? "0" + this.seconds : this.seconds;
  }
};
</script>

<style scoped>
.sections {
  display: flex;
  justify-content: space-between;
}
.timer {
  max-width: 500px;
  background-color: #87ceeb;
  border-radius: 10px;
}
.hidden {
  display: none;
}
.section-button:hover {
  background-color: #f3fafd;
}
</style>
