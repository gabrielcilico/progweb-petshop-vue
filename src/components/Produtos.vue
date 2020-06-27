<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="md-4" v-for="produto in produtos" :key="produto._id">
        <v-card>
          <v-card-title>{{produto.nome}}</v-card-title>
          <v-list-item-content>

          </v-list-item-content>
          <v-list-item-subtitle>Valor Original: • {{produto.valor.toLocaleString('pt-br',{style: 'currency', currency: 'BRL'})}}</v-list-item-subtitle>
          <v-list-item-subtitle v-if="produto.desconto">Desconto: • {{produto.desconto}}</v-list-item-subtitle>
          <v-list-item-subtitle v-if="produto.desconto">Valor com desconto: • {{formataValor(produto)}}</v-list-item-subtitle>

          <v-card-actions>
            <v-btn text>VER FRETE</v-btn>
            <v-btn text>COMPRAR</v-btn>
          </v-card-actions>

        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Produtos',
  data: () => ({
    produtos: [],
  }),
  methods: {
    formataValor(produto) {
      let valorFormatado = produto.valor -(produto.valor * ("0." + produto.desconto.replace("%","")))
      return valorFormatado.toLocaleString('pt-br',{style: 'currency', currency: 'BRL'});
    }
  },
  mounted() {
    axios
      .get('https://server-node-example.herokuapp.com/produtos')
      .then((response) => {
        this.produtos = response.data;
      })
      .catch((error) => console.log(error));
  },
};
</script>
