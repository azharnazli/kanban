<template>
  <v-app>
    <v-content>
      <navbar/>
      <footers/>
    </v-content>
    <router-view>
    </router-view>
  </v-app>
</template>

<script>
import navbar from './components/navbar'
import footers from './components/footer'

export default {
  name: 'App',
  components: {
    navbar,
    footers
  },
  data () {
    return {
      //
    }
  }
}
</script>
