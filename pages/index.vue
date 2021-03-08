<template>
  <v-app app>
    <v-main>
      <v-container class="mx-auto">
        <v-row>
          <v-col cols="8">
            <v-text-field v-model.trim="newTask" placeholder="Введите задачу" color="green" prepend-icon="mdi-message">
          </v-text-field>
        <v-btn
          @click.prevent="newTodo"
          class="pl-9 mx-auto"
          color="yellow"
          text
          plain
          large
          :disabled="disabled"
        >
          Добавить задачу
        </v-btn>
        <v-btn text>
          <v-icon
            @click.prevent="newTodo"
            :disabled="disabled"
            left
            color="#CDDC39"
            class="pl-1"
            x-large
            >
            mdi-plus
          </v-icon>
        </v-btn>
          </v-col>
          
        </v-row>
          
        <v-row>
          <v-col cols="8">
            <v-simple-table fixed-header dense dark>
          <thead>
        <tr>
          <th class="text-left">
            Задача
          </th>
          <v-divider vertical></v-divider>
           <th class="text-left">
           Завершена
           <v-icon @click="removeTask" color="yellow">mdi-minus</v-icon>
          </th>
        </tr>
      </thead>
          <tbody v-for="(todos, index) in todo" :key="index" class="ml-3">
            {{ todos }}
          </tbody>
        </v-simple-table>
          </v-col>
        </v-row>
      <v-app-bar-title class="mt-10">Текущих задач: {{ todo.length }}</v-app-bar-title>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  // Сделать таблицу заместо списков
  // таймиер (время на выполнеение)
  // Добавить иконку редактирования(карандаш)
  // Добавить чекбокс выполнена/ не выполнена

export default {
  data()  {
    return {
      todo: [],
      newTask: '',
      disabled: true,
      index: 1
    }
  },
  methods: {
    newTodo() {
      this.todo.push(this.newTask)
      this.newTask = ''
    },
    removeTask(index) {
      this.todo.splice(index,1)
    }
  },
  watch: {
    newTask () {
      if (this.newTask !== '') {
        console.log(this.disabled)
        this.disabled = false
      } else {
        this.disabled = true
      }
    }
  }
}
</script>
