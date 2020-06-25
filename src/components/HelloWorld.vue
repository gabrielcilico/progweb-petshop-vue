<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">Produtos: {{ produtos }}</v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',

  data: () => ({
    produtos: [],
  }),
  mounted() {
    axios
      .get('https://server-node-example.herokuapp.com/produtos')
      .then((response) => {
        console.log(response);
        this.produtos = response.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>
