<template>
  <div class="home">    
    <Produtos />
  </div>
</template>

<script>
// @ is an alias to /src
import Produtos from "@/components/Produtos.vue";

export default {
  name: "Home",
  components: {
    Produtos
  }
};
</script>
