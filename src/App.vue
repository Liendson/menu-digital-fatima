<script lang="ts">
import CardPessoaComponent, { Profissional } from './components/CardPessoaComponent.vue'
import CardFinderComponent, { Finder } from './components/CardFinderComponent.vue'

export default {
  components: {
    CardPessoaComponent,
    CardFinderComponent
  },
  data: () => ({
    finder: new Finder('img/fatima.png', 'Fátima Lucena', 'Conectando você as melhores soluções do mercado!'),
    profissionais: [
      new Profissional('img/priscrila.png', 'Priscilla Mendonça', 'Administradora Financeira.'),
      new Profissional('img/ere-queiroz.png', 'Erê Queiroz', 'Inovação, Liderança, Mentoria e Consultoria.'),
      new Profissional('img/georgia-lima.png', 'Georgia Lima', 'Estrategista de Comunicação e Oratória.'),
      new Profissional('img/angela-lucena.png', 'Angela Lucena', 'Estética Avançada.'),
      new Profissional('img/gabrielle-lucena.png', 'Gabrielle Lucena', 'Consultora de Imagem Corporativa.'),
      new Profissional('img/mahriana-b.png', 'Mahrianna B', 'Psicóloga de Negócios.'),
      new Profissional('img/francisco-douglas.png', 'Francisco Douglas', 'Terapeuta Constelação Familiar.'),
      new Profissional('img/ryan-galvao.png', 'Ryan Galvão', 'Fotógrafo.'),
    ]
  }),
};
</script>

<template>
  <section class="principal">
    <div class="container">
      <div class="row">
        <CardFinderComponent :finder="finder" />
        <CardPessoaComponent
          v-for="profissional in profissionais"
          :profissional="profissional"
          :key="profissional.nome"/>
      </div>
    </div>
  </section>
</template>