<template>
  <div class="container">
    <p v-if="$fetchState.pending" class="text-center">Carregando...</p>
    <p v-else-if="$fetchState.error" class="text-center">Ocorreu um erro:</p>
    <div class="row">
      <div v-for="nota of notas" :key="nota.id" class="col-md-3">
        <div class="card bg-warning my-3">
          <div class="card-body">
            <h5 class="card-title">{{ nota.titulo }}</h5>
            <p v-if="nota.descricao" class="card-text">
              {{ nota.descricao }}
              teste push dasdasd
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.card {
  min-height: 15rem;
}
</style>

<script>
export default {
  data() {
    return {
      notas: []
    };
  },
  async fetch(){
    this.notas = await this.$axios.get('nota/usuario/3');
  }
};
</script>