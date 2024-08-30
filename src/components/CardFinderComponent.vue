
<template>
  <div class="col-12 text-center mb-2">
    <div class="card-icon text-center mb-3">
      <img :src="finder.img" class="img-padrao" alt="imagem-finder" />
    </div>
    <span class="hint-title">
      <strong>Finder</strong>
    </span>
    <h1 class="title">
      <strong>{{ finder.nome }}</strong>
    </h1>
    <span>{{ finder.descricao }}</span>
  </div>
	<div class="col-12 text-center mb-5">
		<a @click="toInstagram()" class="btn btn-sm btn-social mr-3">
			<em class="fa fa-instagram"></em>
		</a>
		<a @click="toWhatsapp()" class="btn btn-sm btn-social">
			<em class="fa fa-whatsapp"></em>
		</a>
	</div>
</template>
  
<script lang="ts">
import { defineComponent } from "vue";

export class Finder {
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
		urlInstagram: 'https://www.instagram.com/fatima_lucenaoliveira/',
		numeroDoCelular: '5583988666678',
	}),
  props: {
    finder: {
      type: Object as () => Finder,
      required: true,
    },
  },
	methods: {
		toInstagram() {
    	window.location.href = this.urlInstagram;
		},
		toWhatsapp() {
			const montarTexto = () => {
        let texto = 'Olá, Fátima!';
				texto += `\n*Me interessei no seu cardápio de profissionais!*\n`;
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
  