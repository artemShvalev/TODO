<template>
  <v-app app>
    <v-main>
      <v-container>
          <v-text-field placeholder="Введите задачу" color="green" prepend-icon="mdi-message">
          </v-text-field>
        <v-btn class="pl-9 mx-auto" color="yellow" text plain large>
          Добавить задачу
        </v-btn>
        <v-icon left color="red" class="pl-1">mdi-plus</v-icon>
        <!-- Здесь итеррировать v card -->
        <v-card>
          <v-list>
            Привет как дела?
            <v-btn
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
}
</script>
