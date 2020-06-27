<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <h1>Petshopers</h1>
      </div>

      <v-spacer></v-spacer>

      
    </v-app-bar>

    <v-content>
      <Produtos/>
    </v-content>
  </v-app>
</template>

<script>
import Produtos from './components/Produtos';

export default {
  name: 'App',

  components: {
    Produtos,
  },

  data: () => ({
    //
  }),
};
</script>
