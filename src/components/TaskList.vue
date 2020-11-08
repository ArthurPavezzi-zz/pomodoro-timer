<template>
  <div id="task">
    <v-text-field color="black" v-model="newTask" :label="$t('taskList.label')"/>
    <v-btn class="add-task" @click="addNewTask" text>{{ $t('taskList.newTask') }}</v-btn>
    <v-btn text @click="removeAllTasks" v-if="tasks.length > 0">{{ $t('taskList.removeAllTasks') }}</v-btn>
    <v-btn text @click="markAllDone" v-if="tasks.length > 0">{{ $t('taskList.markAllDone') }}</v-btn>
    <ul>
      <li v-for="(task, index) in tasks" :key="task.id" class="task">
        <h3 :class="{ done: task.done }" @click="toggleDone(task)">{{ task.content }}</h3>
        <v-btn class="remove" text @click="removeTask(index)">{{ $t('taskList.remove') }}</v-btn>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TaskList",
  data() {
    return {
      newTask: '',
      tasks: []
    }
  },
  methods: {
    addNewTask() {
      if (this.newTask !== '') {
        this.tasks.push({
          id: Date.now(),
          done: false,
          content: this.newTask,
        });
        this.newTask = '';
      }
    },

    toggleDone(task) {
      task.done = !task.done;
    },

    removeTask(index) {
      this.tasks.splice(index, 1);
    },

    markAllDone() {
      this.tasks.forEach((task) => task.done = true);
    },

    removeAllTasks() {
      this.tasks = [];
    }
  }
}
</script>

<style lang="sass" scoped>
#task
  padding-top: 1em
  padding-bottom: 1em
  font-size: 2em
  width: 50%
  margin: 0 auto
  color: whitesmoke

.add-task
  display: block
  width: 100%
  font-size: 1em
  padding: 10px
  margin: 0.5em

.v-text-field
  width: 450px
  margin: 0 auto
  color: whitesmoke

li
  display: flex
  flex-direction: column
  width: 80%
  margin: 0 auto

h3
  font-size: 28px

.v-btn
  color: whitesmoke
  width: 100%
  padding: 10px

p
  display: block
  width: 100%
  font-size: 1em
  margin: 0.5em

.v-btn
  margin: 0
  padding: 0

.remove
  width: 100%
  margin: 10px 0 0 0

.task
  cursor: pointer

.done
  text-decoration: line-through
</style>