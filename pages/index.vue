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
            color="red"
            class="pl-1"
            x-large
            >
            mdi-plus
          </v-icon>
        </v-btn>
        <!-- Здесь итеррировать v card -->
        <v-card v-for="(todos, index) in todo" :key="index">
          <v-list>
            {{ todos }}
            <v-btn
              @click="removeTask(index)"
              class="mx-2"
              fab
              dark
              small
              color="primary"
            >
              <v-icon dark>
                mdi-minus
              </v-icon>
            </v-btn>
          </v-list>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>

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
