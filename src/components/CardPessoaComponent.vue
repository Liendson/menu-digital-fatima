
<template>
  <div class="col-6 mb-5">
    <div class="card-icon text-center">
      <img
        class="img-padrao"
        alt="imagem-profissional"
        :src="profissional.img"
        @click="toWhatsapp(profissional.nome)"
      />
    </div>
    <div class="card-text text-center d-flex flex-column mt-3">
      <span class="hint-title"><strong>{{ profissional.nome }}</strong></span>
      <span>{{ profissional.descricao }}</span>
    </div>
  </div>
</template>
  
<script lang="ts">
import { defineComponent } from "vue";

export class Profissional {
  img!: string;
  nome!: string;
  descricao!: string;
  constructor(img: string, nome: string, descricao: string) {
    this.img = img;
    this.nome = nome;
    this.descricao = descricao;
  }
}

export default defineComponent({
  data: () => ({
		numeroDoCelular: '5583988666678',
	}),
  props: {
    profissional: {
      type: Object as () => Profissional,
      required: true,
    },
  },
  methods: {
    toWhatsapp(nomeDoProfissional: string) {
      const montarTexto = () => {
        let texto = 'Olá, Fátima!';
        texto += `\n*Me interessei no profissional ${nomeDoProfissional}!*\n`;
        texto += '\n*Poderia me passar mais informações?*';
        return texto;
      }
      const encode = encodeURI(montarTexto());
      const urlWhatsapp = `https://wa.me/${this.numeroDoCelular}?text=${encode}`;
      window.location.href = urlWhatsapp;
    },
  },
});
</script>
  