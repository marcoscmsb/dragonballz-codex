<template>
<div class="flex justify-end p-10">
  <app-dark-mode></app-dark-mode>
</div>
  <h1 class="text-center text-4xl mt-20 mb-10 font-bold text-gray-50">
    Dragpon Ball Z
  </h1>

  <form class="flex justify-center flex-wrap">
    <div class="flex border-4 border-blue-500 rounded-lg mr-5 overflow-hidden">
      <span class="text-sm text-white px-4 py-2 bg-blue-500 whitespace-no-wrap"
        >Nome:</span
      >
      <input
        class="px-4 py-2 w-full outline-none"
        type="text"
        v-model="personagem.nome"
        placeholder="Nome do personagem"
      />
    </div>
    <div class="flex border-4 border-blue-500 rounded-lg overflow-hidden mr-5">
      <span class="text-white px-4 py-2 bg-blue-500 whitespace-no-wrap"
        >Imagem:</span
      >
      <input
        class="px-4 py-2 w-full outline-none"
        type="text"
        v-model="personagem.imagem"
        placeholder="Imagem do personagem"
      />
    </div>
    <button
      class="bg-blue-700 px-10 text-white uppercase rounded-lg"
      @click="salvarPersonagem"
      type="button"
    >
      Salvar
    </button>
  </form>

 

  <section class="flex flex-wrap p-10 justify-evenly">
    <app-personagem-card
      class="mb-5"
      :personagem="p"
      v-for="p in personagens"
      :key="p.nome"
    ></app-personagem-card>
  </section>
</template>

<script>
import AppDarkMode from "./components/AppDarkMode.vue";
import AppPersonagemCard from "./components/AppPersonagemCard.vue";
import axios from "axios";
export default {
  components: {
    AppPersonagemCard,
    AppDarkMode,
  },
  data() {
    return {
      personagem: {},
      personagens: [],
    };
  },
  methods: {
    async buscarTodosPersonagens() {
      //requisição GET para API
      const resp = await axios.get("http://localhost:3001/personagens");
      this.personagens = resp.data;
    },
    async salvarPersonagem() {
      const resp = await axios.post(
        "http://localhost:3001/personagens",
        this.personagem
      );
      alert(resp.data.mensagem);
      this.buscarTodosPersonagens();
      this.personagem = {};
    },
  },
  mounted() {
    this.buscarTodosPersonagens();
  },
};
</script>
