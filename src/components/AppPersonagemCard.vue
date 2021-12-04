<template>
    <div  class="bg-blue-500 w-56 h-64 shadow-xl overflow-hidden border-4 border-blue-500 radi ">
    
      <div ref="imagem" class="imagem"></div>
      <h2 class="p-5 font-bold tex-xl text-center bg-blue-500 text-white">{{personagem.nome}}</h2>
      </div>
</template>
<script>
export default {
    props: ['personagem'],
    mounted() {
        this.$refs.imagem.style.backgroundImage = `url(${this.personagem.imagem})`
    }
}
</script>
<style  scoped>
.imagem{
    height: 180px;
    width: 100%;
    background-color:  rgb(20, 43, 255);
    background-size:  cover;
    background-position: center;
}

</style>