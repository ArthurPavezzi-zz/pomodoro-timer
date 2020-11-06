<template>
  <v-dialog v-model="dialog" persistent max-width="600px">
    <v-card>
      <v-card-title>
        <span class="headline">Settings</span>
      </v-card-title>

      <v-card-text>
        <v-text-field type="number" v-for="(timer, index) in updatedTimers" :key="index"
                      :label="`${timers[index].name}`" v-model="updatedTimers[index]"/>
      </v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="blue darken-1" text @click="closeDialog">Close</v-btn>
        <v-btn color="blue darken-1" text @click="saveSettings(updatedTimers)">Save</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "SettingsDialog",
  props: {
    dialog: {
      type: Boolean,
      require: true
    },
    closeDialog: {
      type: Function,
      require: true
    },
    timers: {
      type: Array,
      require: true
    },
    saveSettings: {
      type: Function,
      require: true
    }
  },
  data() {
    return {
      updatedTimers: []
    }
  },
  mounted() {
    this.updatedTimers = this.timers.map((timer) => {
      return timer.minutes;
    });
  }
}
</script>

<style scoped>

</style>