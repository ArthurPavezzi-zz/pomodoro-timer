<template>
  <v-main id="about">
    <v-row>
      <v-col sm="7" offset-sm="3">
        <h2>A responsive and customizable app to boost your productivity!</h2>
        <h3>What is the Pomodoro Technique?</h3>
        <blockquote>The Pomodoro Technique is a time management method developed by Francesco Cirillo in the late
          1980s. The technique uses a timer to break down work into intervals, traditionally 25 minutes in length,
          separated by short breaks. Each interval is known as a pomodoro, from the Italian word for 'tomato', after 
          the tomato-shaped kitchen timer that Cirillo used as a university student. -
          <a href="https://en.wikipedia.org/wiki/Pomodoro_Technique">Wikipedia</a>
        </blockquote>
        <h3>How to use Pomodoro Timer?</h3>
        <ol type="1">
          <li><b>Add tasks</b> to work on today</li>
          <li><b>Select a task</b> to work on</li>
          <li><b>Start timer and focus</b> on the task for 25 minutes</li>
          <li><b>Take a break</b> for 5 minutes when the alarm ring</li>
          <li><b>Iterate</b> until you finish the tasks</li>
        </ol>
        <h3>Features</h3>
        <ul>
          <li><b>Responsive design</b> that works with desktop and mobile</li>
          <li><b>Color transition</b> to switch moods between work time and rest time</li>
          <li><b>Audio notification</b> at the end of a timer period</li>
          <li><b>Customizable timer</b> intervals to suit your preference</li>
        </ul>
      </v-col>
    </v-row>
  </v-main>
</template>

<script>
export default {
name: "About"
}
</script>

<style lang="sass" scoped>
#about
  background-color: whitesmoke
  margin: 0 auto

h2
  margin: 20px 0

h3
  margin: 20px 0 10px 0
  &::after
    content: ''
    border-bottom: 3px solid #F05B56
    width: 10px
    display: block

blockquote a
  color: #F05B56
  text-decoration: none
</style>