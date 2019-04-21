<template>
  <v-layout row>
    <v-flex xs12 >
      <v-card
      v-for="(task, index) in data"
      :key="index"
      >
        <v-card-title primary-title>
            <h1 class="text-xs-center">{{ task.title}}</h1>
        </v-card-title>
        <v-slide-y-transition>
          <v-card-text >
            <h4>Point : {{ task.point}}</h4>
            <h4>Assigned To : {{ task.assign}}</h4>
          </v-card-text>
        </v-slide-y-transition>

        <v-card-actions>
          <modal
          :point="task.point"
          :assignTo="task.assign"
          :title="task.title"
          :description="task.description"
          :state="task.state"
          :cardId="task.id"
          />
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
import modal from './cardModal'
export default {
  props: ['data'],
  components : {
    modal
  }
}
</script>