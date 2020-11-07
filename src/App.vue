<template>
  <v-app id="main">
    <nav id="navigation">
      <div class="logo">
        <a href="/"><img src="../public/pomodoro.png" alt="">
          <p>Pomodoro Timer</p>
        </a>
      </div>
    </nav>
    <v-main>
      <v-container>
        <v-row>
          <v-col sm="6" offset-sm="3">
            <Pomodoro :dialog="dialog" :closeDialog="closeDialog" @changeBgColor="changeBgColor"/>
          </v-col>
          <v-btn color="secondary" dark small top right fab @click="dialog = true">
            <v-icon>mdi-cog-outline</v-icon>
          </v-btn>
        </v-row>
      </v-container>
    </v-main>
    <TaskList/>
    <About/>
  </v-app>
</template>

<script>
import Pomodoro from "@/components/Pomodoro";
import TaskList from "@/components/TaskList";
import About from "@/components/About";

export default {
  name: 'App',
  components: {
    Pomodoro,
    TaskList,
    About
  },

  data() {
    return {
      dialog: false
    }
  },
  methods: {
    closeDialog() {
      this.dialog = false
    },
    changeBgColor(color) {
      document.getElementById('main').style.backgroundColor = color;
    }
  }
};
</script>

<style lang="sass" scoped>
#main
  background-color: #F05B56
  transition-duration: 0.5s

#navigation
  display: flex
  padding: 10px 5%
  color: whitesmoke

img
  width: 60px

.logo
  font-size: 24px

a
  display: flex
  text-decoration: none

p
  color: whitesmoke
  margin: 0
  padding: 15px 0 10px 10px
</style>