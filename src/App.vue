<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row>
          <v-col sm="6" offset-sm="3">
            <Pomodoro :dialog="dialog" :closeDialog="clodeDialog"/>
          </v-col>
          <v-btn color="secondary" dark small top right fab
          @click="dialog = true">
            <v-icon>mdi-cog-outline</v-icon>
          </v-btn>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import Pomodoro from "@/components/Pomodoro";

export default {
  name: 'App',
  components: {
    Pomodoro
  },

  data() {
    return {
      dialog: false
    }
  },
  methods: {
    clodeDialog() {
      this.dialog = false
    }
  }
};
</script>
