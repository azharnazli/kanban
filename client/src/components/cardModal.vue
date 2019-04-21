<template>
  <v-layout row justify-center>
    <v-dialog v-model="dialog" persistent max-width="390">
      <template v-slot:activator="{ on }">
        <v-btn color="primary" dark v-on="on">Show Detail</v-btn>
      </template>
      <v-card>
        <v-card-title class="">{{ title }}</v-card-title>
        <v-card-text>description: {{ description }}</v-card-text>
        <v-card-text>point: {{ point }}</v-card-text>
        <v-card-text>status: {{ state }}</v-card-text>
        <v-card-actions>
          <v-btn color="red darken-1" flat @click="dialog = false">close</v-btn>
          <v-btn @click="deleteData" color="red darken-1" flat >delete</v-btn>
          <v-btn v-if="button2 != null" @click="changeDown"  color="green darken-1" flat >{{ button2 }}</v-btn>
          <v-spacer></v-spacer>
          <v-btn color="primary darken-1" flat
          v-if="button1 != null " 
          @click="changeUp" 
          >{{ button1 }}</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-layout>
</template>
<script>
  import db from '../firebase.js'
  export default {
    props: ['point', 'assignTo', 'title', 'description', 'state','cardId'],
    data() {
      return {
        dialog: false,
        button1: '',
        button2: ''
      }
    },
    created() {
      if (this.state == 'prelog') {
        this.button1 = 'todo'
        this.button2 = null
      } else if (this.state == 'todo') {
        this.button1 = 'doing'
        this.button2 = 'prelog'
      } else if (this.state == 'doing') {
        this.button1 = 'done'
        this.button2 = 'todo'
      } else if (this.state == 'done') {
        this.button1 = null
        this.button2 = 'doing'
      }
    },
    methods : {
      changeUp() {
       db.collection('kanban').doc(this.cardId).update({
         state : this.button1
       })
        .then((data) => {
          this.dialog = false
        })
      },
      changeDown() {
       db.collection('kanban').doc(this.cardId).update({
         state : this.button2
       })
        .then((data) => {
          this.dialog = false
        })
      },
      deleteData() {
        db.collection('kanban').doc(this.cardId).delete()
          .then((data)=> {
            console.log(data)
            this.dialog = false
          })
      }
    }
  }

</script>
