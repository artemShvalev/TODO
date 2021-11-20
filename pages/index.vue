<template>
  <v-app app >
    <v-main>
      <v-app-bar-title 
       class="mt-10 text-center" 
      :class="{updateCurrentTasks: isUpdate, updateEqFour: isUpdateFour }"
      >
       Текущих задач: 
      {{ todo.length }}
      </v-app-bar-title>

      <v-container 
        class="d-sm-flex justify-center">

        <v-row 
        class="ml-16 mt-20">

          <v-col cols="8">

            <v-text-field 
            v-model.trim="newTask" 
            placeholder="Введите задачу" 
            color="green" 
            prepend-icon="mdi-message"/>

          <!-- select -->
            <v-select
              max-width="100"
              color="blue"
              label="Установить время"
              hint="У тебя есть пара минут"
              prepend-icon="mdi-timer"
              :items="itemsTimerNumber"
              :disabled="disabled"
            >
            </v-select>
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
            <v-simple-table 
            fixed-header 
            dense 
            dark 
            height="500"
            >
          <thead>
        <tr>
          <th class="text-left">
            Задача
          </th>
          <v-divider vertical/>
          <th>
            Время: {{currentMinutes}}
          </th>
        </tr>
      </thead>
          <v-divider vertical/>
            <client-only>
          <tbody v-for="(todos, index) in todo" :key="index">
            <tr>
              <td @click="removeTask">
            {{index + 1}} : {{ todos }}
              </td>
            </tr>
          <v-divider/>
          </tbody>
            </client-only>
        </v-simple-table>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  //TODO:
  // Если больше 3 задач сменить цвет 
  // таймер (время на выполнеение)
  // Добавить иконку редактирования(карандаш)
  // Добавить чекбокс выполнена/ не выполнена
  // Добавить rating to tasks
  // Когда вышло время отображать время крассным


export default {
  data()  {
    return {
      todo: [],
      newTask: '',
      disabled: true,
      index: 1,
      currentMinutes: 60,
      itemsTimerNumber: [
        5 + '  минут \n',
        10 + ' минут \n',
        20 + ' минут \n',
        30 + ' минут \n',
        40 + ' минут \n',
        50 + ' минут \n',
        60 + ' минут \n'
      ],
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
  computed: {
    isUpdate (isUpdate) {
      if (this.todo.length > 0) {
        return isUpdate = true;
      }
    },
    isUpdateFour (isUpdateFour) {
      if (this.todo.length > 3) {
        return isUpdateFour = true;
      }
    }

  },
  watch: {
    newTask () {
      this.disabled = this.newTask === '';
    }
  },
}
</script>

<style scoped>
  .updateCurrentTasks{
    color:rgb(231, 172, 231);
  }
  .updateEqFour{
    color:rgb(238, 123, 139);
  }
</style>
