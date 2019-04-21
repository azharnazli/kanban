<template>
  <v-dialog v-model="dialog" persistent max-width="390">
    <template v-slot:activator="{ on }">
      <v-btn dark v-on="on">new task</v-btn>
    </template>
    <v-card>
      <template>
        <form style="padding: 15px;">
          <v-text-field v-model="title" label="title" required ></v-text-field>
          <v-text-field v-model="description" label="description" required></v-text-field>
          <v-text-field type="number" v-model="point" label="point" required></v-text-field>
          <v-text-field type="number" v-model="assign" label="assign" required></v-text-field>

          <v-btn 
          @click="dialog = false"
          v-on:click="addNewTask"
          >submit</v-btn>
          <v-btn 
          @click="dialog = false"
          v-on:click="resetForm"
          >clear</v-btn>
        </form>
      </template>

    </v-card>
  </v-dialog>
</template>
<script>
import db from '../firebase';
  export default {
    data() {
      return {
        dialog: false,
        title: '',
        description: '',
        point: 0,
        assign: 0,
      }
    },
    methods: {
      addNewTask() {
        db.collection('kanban').add({
          title : this.title,
          description : this.description,
          point : this.point,
          assign : this.assign,
          state: 'prelog'
        })
      },
      resetForm() {
        this.title = ''
        this.description = ''
        this.point = 0
        this.assign = 0
      }
    }
  }

</script>
