<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/logo.svg')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">Todo List</h1>
      </v-col>

      <v-col cols="12" class="mb-5">
        <v-text-field
          v-model="newTask"
          label="Add a new task"
          @keyup.enter="addTask"
          outlined
        />
        <v-btn @click="addTask" color="primary">Add</v-btn>
      </v-col>

      <v-col cols="12">
        <v-list>
          <v-list-item-group>
            <v-list-item
              v-for="(task, index) in tasks"
              :key="index"
            >
              <v-list-item-content>
                <v-list-item-title>{{ task.text }}</v-list-item-title>
              </v-list-item-content>
              <v-list-item-action>
                <v-btn @click="removeTask(index)" icon>
                  <v-icon>mdi-delete</v-icon>
                </v-btn>
              </v-list-item-action>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'TodoList',
  data: () => ({
    newTask: '',
    tasks: [],
  }),
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
}
</script>

<style scoped>
.v-list-item {
  display: flex;
  justify-content: space-between;
}
</style>
