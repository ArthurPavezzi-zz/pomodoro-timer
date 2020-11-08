<template>
  <v-app id="main">
    <nav id="navigation">
      <div class="logo">
        <router-link to="/"><img src="../../public/pomodoro.png" alt="">
          <p>{{ $t('home.title') }}</p>
        </router-link>
      </div>
      <label for="language">{{ $t('home.language')}}:</label>
      <select name="language" id="language" v-model="lang" @change="handleLanguageChange($event)">
        <option id="en" value="en" selected>English</option>
        <option id="pt" value="pt-br">Português</option>
      </select>
    </nav>
    <v-main>
      <v-container>
        <v-row>
          <v-col sm="6" offset-sm="3">
            <Pomodoro :dialog="dialog" :closeDialog="closeDialog" @changeBgColor="changeBgColor"/>
          </v-col>
          <v-btn color="secondary" dark small top right fab @click="dialog = true">
            <v-icon>mdi-cog</v-icon>
          </v-btn>
        </v-row>
      </v-container>
    </v-main>
    <TaskList/>
    <About/>
    <Footer/>
  </v-app>
</template>

<script>
import Pomodoro from "@/components/Pomodoro";
import TaskList from "@/components/TaskList";
import About from "@/components/About";
import Footer from "@/components/Footer";

export default {
  name: 'App',
  components: {
    Pomodoro,
    TaskList,
    About,
    Footer
  },
  data() {
    return {
      dialog: false,
      lang: localStorage.getItem('lang') || 'en'
    }
  },
  methods: {
    closeDialog() {
      this.dialog = false
    },
    changeBgColor(color) {
      document.getElementById('main').style.backgroundColor = color;
      document.getElementById('en').style.backgroundColor = color;
      document.getElementById('pt').style.backgroundColor = color;
    },
    handleLanguageChange(event) {
      this.$root.$i18n.locale = event.target.value
    }
  }
};
</script>

<style lang="sass" scoped>
#main
  background-color: #f05b56
  transition-duration: 0.5s

#navigation
  display: flex
  padding: 10px 5%
  color: whitesmoke

img
  width: 60px

.logo
  font-size: 24px
  width: 100%
  display: flex
  flex-direction: row

a
  display: flex
  text-decoration: none

p
  color: whitesmoke
  margin: 0
  padding: 15px 0 10px 10px

label
  padding: 18px
  font-size: 20px

select
  font-size: 20px
  color: whitesmoke

  option
    background-color: rgb(240, 81, 86)

Footer
  background-color: #F05B56
</style>