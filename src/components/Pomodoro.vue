<template>
  <v-card class="mt-8">
    <v-tabs @change="changeCurrentTimer" v-model="currentTimer" grow>
      <v-tab v-for="timer in timers" :key="timer.name">
        {{ timer.name }}
      </v-tab>
    </v-tabs>
    <v-card class="pa-5 d-flex flex-column justify-center align-center" flat>
      <h1 class="time">{{ `${displayMinutes}:${displaySeconds}` }}</h1>
    </v-card>
    <div class="button-group">
      <v-btn @click="startTime" color="primary">
        <v-icon left small>mdi-play-circle-outline</v-icon>
        Start
      </v-btn>
      <v-btn @click="stopTime" color="error">
        <v-icon left small>mdi-stop-circle-outline</v-icon>
        Stop
      </v-btn>
      <v-btn @click="resetTime(timers[currentTimer].minutes)" :disabled="isRunning">
        <v-icon left small>mdi-restart</v-icon>
        Reset
      </v-btn>
    </div>
    <SettingsDialog :dialog="dialog" :closeDialog="closeDialog"
                    :timers="timers" :saveSettings="saveSettings"/>
  </v-card>
</template>

<script>
import SettingsDialog from "./SettingsDialog";

export default {
  name: "Pomodoro",
  components: {
    SettingsDialog
  },
  props: {
    dialog: {
      type: Boolean,
      require: true
    },
    closeDialog: {
      type: Function,
      require: true
    }
  },
  data() {
    return {
      isRunning: false,
      timerInstance: null,
      totalSeconds: 25 * 60,
      currentTimer: 0,
      timers: [
        {
          name:'Pomodoro',
          minutes: 25
        },
        {
          name:'Short Break',
          minutes: 5
        },
        {
          name:'Long Break',
          minutes: 10
        },
      ]
    }
  },
  computed: {
    displayMinutes() {
      const minutes = Math.floor(this.totalSeconds / 60);
      return this.formatTime(minutes);
    },
    displaySeconds() {
      const seconds = this.totalSeconds % 60;
      return this.formatTime(seconds);
    }
  },
  methods: {
    formatTime(time) {
      return (time < 10) ? '0' + time : time.toString();
    },
    startTime() {
      this.stopTime();
      this.isRunning = true;
      this.timerInstance = setInterval(() => {
        if(this.totalSeconds <= 0) {
          this.stopTime();
          return null;
        }
        this.totalSeconds--;
      }, 1000);
    },
    stopTime() {
      this.isRunning = false;
      clearInterval(this.timerInstance);
    },
    resetTime(minutes) {
      this.stopTime();
      this.totalSeconds = minutes * 60;
    },
    changeCurrentTimer(index) {
      this.resetTime(this.timers[index].minutes);
    },
    saveSettings(updatedTimers) {
      this.timers = this.timers.map((timer, i) => {
        return { ...timer, minutes: parseInt(updatedTimers[i]) }
      })
      this.totalSeconds = this.timers[this.currentTimer].minutes * 60;
      this.closeDialog()
    }
  }
}
</script>

<style lang="sass" scoped>
.v-card
  width: 450px

.button-group
  padding-bottom: 20px
  text-align: center

.v-btn
  margin: 0 10px

.time
  font-size: 80px
  font-weight: 400
  text-align: center

.v-btn
  text-align: center
</style>