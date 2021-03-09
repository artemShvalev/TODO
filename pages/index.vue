<template>
  <v-app app>
    <v-app-bar-title class="mt-10">Текущих задач: {{ todo.length }}</v-app-bar-title>
    <v-main>
      <v-container>
        <v-row>
          <v-col cols="8">
            <v-text-field v-model.trim="newTask" placeholder="Введите задачу" color="green" prepend-icon="mdi-message"/>
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
            <v-simple-table fixed-header dense dark height="500">
          <thead>
        <tr>
          <th class="text-left">
            Задача
          </th>
          <v-divider vertical/>
          <th v-if="timer">
            Время: {{currentMinutes}} сек
          </th>
        </tr>
      </thead>
          <v-divider vertical/>
          <tbody v-for="(todos, index) in todo" :key="index">
            <tr>
              <td @click="removeTask" >
            {{ todos }}
              </td>
            </tr>
          </tbody>
        </v-simple-table>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
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
      currentMinutes: 60
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
        this.disabled = false
      } else {
        this.disabled = true
      }
    }
  },
  computed: {
    timer: function() {
      setTimeout(() => {
        for(let i = 61; this.currentMinutes !== 0;  i-- ) {
          this.currentMinutes
          console.log(this.currentMinutes)
        }
      },1000)
    }
  }
}
</script>
