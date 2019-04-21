<template>
  <v-layout row>
      <v-card style="width: 600px" >
        <v-card-title primary-title>
          <v-container style="margin-bottom: 10px;" class="fluid red">
            <h1 class="text-xs-center">Prelog</h1>
          </v-container>
            <card
            :data="prelog"
            />
        </v-card-title>
      </v-card>
      <v-card style="width: 600px" >
        <v-card-title primary-title>
          <v-container style="margin-bottom: 10px;" class="fluid orange">
            <h1 class="text-xs-center">Todo</h1>
          </v-container>
            <card
            :data="todo"
            />
        </v-card-title>
      </v-card>
      <v-card style="width: 600px" >
        <v-card-title primary-title>
          <v-container style="margin-bottom: 10px;" class="fluid primary">
            <h1 class="text-xs-center">on-Doing</h1>
          </v-container>
            <card
            :data="doing"
            />
        </v-card-title>
      </v-card>

      <v-card style="width: 600px" >
        <v-card-title primary-title>
          <v-container style="margin-bottom: 10px;" class="fluid green">
            <h1 class="text-xs-center">Done</h1>
          </v-container>
            <card
            :data="done"
            />
        </v-card-title>
      </v-card>
  </v-layout>
</template>
<script>
  import card from '../components/card'

  export default {
    props: ['prelog','todo','doing','done'],
    components: {
      card
    }
  }

</script>
