<template>
  <v-app app>
    <v-main>
      <v-container>
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
        <!-- Здесь итеррировать v card -->
        <v-simple-table fixed-header>
          <thead>
        <tr>
          <th class="text-left">
            Задача
          </th>
            <v-divider vertical></v-divider>
          <th class="text-left" :id="id">
             Ожидает завершения
          </th>
          <v-divider vertical></v-divider>
           <th class="text-left">
           Завершена
          </th>
          <v-divider vertical></v-divider>
        </tr>
      </thead>
          <tbody v-for="(todos, index) in todo" :key="index">
            {{ todos }}
          </tbody>

        </v-simple-table>
      </v-container>
      <v-spacer />
      <v-app-bar-title>Текущих задач: {{ todo.length }}</v-app-bar-title>
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
      index: 1,
    }
  },
  methods: {
    newTodo() {
      this.todo.push(this.newTask)
      this.newTask = ''
    },
    removeTask(index) {
      this.todo.splice(index,1)
      console.log(index)
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
