<template>
  <v-container>
    <v-layout row wrap>
      <cardContent :prelog="prelog" :todo="todo" :doing="doing" :done="done" />
    </v-layout>
  </v-container>
</template>

<script>
  import cardContent from '../components/cardContent.vue'
  import db from '../firebase.js'

  export default {
    components: {
      cardContent
    },
    data() {
      return {
        prelog: [],
        todo: [],
        doing: [],
        done: []
      }
    },
    methods: {
      checkDb() {
        db.collection('kanban')
          .onSnapshot((doc) => {
            this.prelog = [],
              this.todo = [],
              this.doing = [],
              this.done = []
            doc.forEach((task) => {
              this[`${task.data().state}`].push({
                id: task.id,
                ...task.data()
              })
            })
          })


      }
    },
    created() {
      this.checkDb()
    }
  }

</script>
