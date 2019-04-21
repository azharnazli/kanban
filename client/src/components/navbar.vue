<template>
  <v-card color="grey lighten-4" flat tile>
    <v-toolbar dense>
      <v-toolbar-title>KANBANS</v-toolbar-title>

      <v-spacer></v-spacer>
      <newTask />
    </v-toolbar>
  </v-card>
</template>
<script>
import newTask from './newTask'
export default {
  components : {
    newTask
  }
}
</script>
