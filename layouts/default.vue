<template>
  <v-app dark>
    <AppToolBar/>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import AppToolBar from './AppToolBar'

export default {
  data() {
    return {};
  },
  components:{
    AppToolBar,
  }
}
</script>
