<template>
  <div class="timer">
    <div class="sections">
      <button @click="pomodoroTime">Pomodoro</button>
      <button @click="shortBreakTime">Short Break</button>
      <button @click="longBreakTime">Long Break</button>
    </div>
    <h1 class="time">{{minutes}} : {{seconds}}</h1>
    <button v-if="isRunning === false" @click="start" class="control">START</button>
    <button v-else @click="stop" class="control">STOP</button>
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
          _this.stop();
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
    }
  },
  created: function() {
    this.minutes = this.minutes < 10 ? "0" + this.minutes : this.minutes;
    this.seconds = this.seconds < 10 ? "0" + this.seconds : this.seconds;
  }
};
</script>

<style scoped>
button {
  margin-top: 10px;
  color: white;
  background: none;
  height: 25px;
  font-size: 22px;
  border-radius: 7px;
  text-align: center;
  box-sizing: unset;
  border: none;
  outline: none;
}
button:hover {
  background-color: #45b3e0;
}
.time {
  font-size: 100px;
  margin: 25px;
}
.timer {
  width: 480px;
  background-color: #87ceeb;
  border-radius: 10px;
  text-align: center;
  display: block;
}
.hidden {
  display: none;
}
.section-button:hover {
  background-color: #f3fafd;
}
.control {
  margin-top: 0px;
  margin-bottom: 10px;
}

@media screen and (min-device-width: 10px) and (max-device-width: 479px) {
  .timer {
    width: 100%;
  }
  .time {
    margin: 2%;
    font-size: 45px;
  }
  .button {
    height: px;
  }
}
</style>
