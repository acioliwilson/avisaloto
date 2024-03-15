<template>
  <div class="container" id="bodyContent">
    <div class="feature" v-if="data">
      <img src="@/assets/clover.png" alt="">
      <h1>{{ data.megasena.tituloModalidade }}</h1>
      <small v-if="data.megasena.acumuladaProxSorteio">Acumulou!</small>
      <p>Sorteio {{ data.megasena.proxConcurso }} - <strong>{{ data.dataProxSorteio }}</strong></p>
      <p class="value">{{ data.megasena.valorEstimadoProxConcurso }}</p>
      <div class="buttons">
        <router-link to="/" class="default-outline-light">Saiba mais</router-link>
        <a href="#" class="default-fill-light">Jogar agora</a>
      </div>
    </div>
  </div>

  <img src="@/assets/waves.png" style="margin: 30px auto; display: table;">

  <section class="container" v-if="data">
    <h2 class="featured-heading">Destaques</h2>
    <article class="featured-articles">
      <p class="title">Sorteio Histórico da {{ data.lotofacil.tituloModalidade }}: Prêmio de {{ data.lotofacil.valorSorteado }} é Conquistado no Concurso {{ data.lotofacil.concurso }}</p>
      <p class="description">Uma noite memorável para os amantes da <a href="#" target="_blank">{{ data.lotofacil.tituloModalidade }}</a>! O Espaço da Sorte, localizado em São Paulo, SP, foi palco do aguardado sorteio do Concurso {{ data.lotofacil.concurso }} da {{ data.lotofacil.tituloModalidade }}, que não decepcionou os participantes ávidos por uma chance...</p>
      <router-link to="/" class="article-btn">Continuar lendo</router-link>
    </article>
    <span class="divisor"></span>
    <article class="featured-articles">
      <p class="title">Sorteio Histórico da {{ data.maismilionaria.tituloModalidade }}: Prêmio de {{ data.maismilionaria.valorSorteado }} é Conquistado no Concurso {{ data.maismilionaria.concurso }}</p>
      <p class="description">Uma noite memorável para os amantes da <a href="#" target="_blank">{{ data.maismilionaria.tituloModalidade }}</a>! O Espaço da Sorte, localizado em São Paulo, SP, foi palco do aguardado sorteio do Concurso {{ data.maismilionaria.concurso }} da {{ data.maismilionaria.tituloModalidade }}, que não decepcionou os participantes ávidos por uma chance...</p>
      <router-link to="/" class="article-btn">Continuar lendo</router-link>
    </article>
    <button class="default-dark-btn">Ver todos</button>
  </section>

  <section class="container" v-if="data">
    <h2 class="results-heading">Resultados</h2>
    <article class="results">
      <div class="results__header">
        <div>
          <h2>{{ data.megasena.tituloModalidade }}</h2>
          <p>Sorteio {{ data.megasena.concurso }}</p>
        </div>
        <div>
          <p>Valor Sorteado:</p>
          <h3>{{ data.megasena.valorSorteado }}</h3>
        </div>
      </div>
      <div class="results__body">
        <div class="numbers">
          <div class="number" v-for="num in data.megasena.dezenasSorteadas" :key="num">{{ num }}</div>
        </div>
      </div>
    </article>
    <button class="default-dark-btn">Ver todos</button>
  </section>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      data: null,
    }
  },
  async mounted() {
    try {
      const response = await axios.get('https://resultados-loterias-json.vercel.app/api/resultados')
      this.data = response.data
    } catch (error) {
      console.error('Erro ao carregar dados:', error)
    }
  }
}
</script>

<style scoped>
@media screen and (max-width: 800px) {
  #bodyContent { margin-top: 75px; }
}

/*
  Feature section
*/
.feature {
  background: #372B6B;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #FFF;
  width: 100%;
  min-height: 400px;
}
.feature img {
  width: 30px !important;
  height: auto;
}
.feature h1 {
  font-family: 'Raleway', sans-serif;
  font-size: 45px;
  color: #FFF;
  line-height: normal;
  font-weight: 800;
}
.feature small {
  font-family: 'Raleway', sans-serif;
  font-size: 15px;
  font-weight: 800;
  padding: 7px 20px;
  border-radius: 100px;
  background: #FFBC0F;
  margin: 10px 0 0 0;
}
.feature p {
  font-family: 'Raleway', sans-serif;
  font-size: 20px;
  margin: 10px 0;
}
p.value {
  margin: 0;
  font-family: 'Raleway', sans-serif;
  font-size: 45px;
  font-weight: 800;
  line-height: normal;
}
.buttons {
  display: flex;
  justify-content: center;
  gap: 30px;
  width: 100%;
  margin-top: 20px;
}
.default-outline-light {
  border-radius: 100px;
  border: 1.4px solid #FFF;
  font-size: 17px;
  font-weight: 500;
  font-family: 'Raleway', sans-serif;
  color: #FFF;
  text-decoration: none;
  padding: 10px 20px;
  transition: .3s ease all;
}
.default-outline-light:hover {
  background: #7c63ec;
  border-color: #7c63ec;
  color: #FFF;
}
.default-fill-light {
  border-radius: 100px;
  border: 1.4px solid #FFF;
  background: #FFF;
  font-size: 17px;
  font-weight: 500;
  font-family: 'Raleway', sans-serif;
  color: #372B6B;
  text-decoration: none;
  padding: 10px 20px;
  transition: .3s ease all;
}
.default-fill-light:hover {
  background: #7c63ec;
  border-color: #7c63ec;
  color: #FFF;
}

/*
  Featured Articles
*/
h2.featured-heading, h2.results-heading {
  font-family: 'Raleway', sans-serif;
  font-size: 25px;
  font-weight: 800;
  color: #000;
  margin: 0 0 20px 0;
}
.featured-articles {
  border: 1px solid #EAEAEA;
  background: #FFF;
  border-radius: 15px;
  padding: 20px 30px;
}
.featured-articles p.title {
  font-size: 20px;
  font-weight: 800;
  font-family: 'Raleway', sans-serif;
  color: #000;
}
.featured-articles p.description {
  font-weight: 400;
  font-family: 'Raleway', sans-serif;
  font-size: 17px;
  line-height: 1.5;
  margin-top: 0;
}
.article-btn {
  text-decoration: none;
  color: #372B6B;
  border: 1.4px solid #372B6B;
  border-radius: 100px;
  padding: 13px 20px;
  font-weight: 500;
  font-family: 'Raleway', sans-serif;
  display: table;
  margin-top: 20px;
  transition: .4s ease all;
}
.article-btn:hover {
  background: #7c63ec;
  color: #FFF;
  border-color: #7c63ec;
  box-shadow: 2px 2px 10px rgba(124, 99, 236, .3);
}
p a {
  font-weight: 500;
}
span.divisor {
  width: 150px;
  height: 2px;
  border-radius: 10px;
  background: #EAEAEA;
  margin: 20px auto;
  display: table;
}
.default-dark-btn {
  color: #FFF;
  font-size: 17px;
  font-weight: 500;
  font-family: 'Raleway', sans-serif;
  padding: 10px 20px;
  border-radius: 100px;
  background: #333;
  border: 1px solid #333;
  margin: 30px auto;
  display: table;
  transition: .4s ease all;
}
.default-dark-btn:hover {
  background: #000;
  border-color: #000;
}
.results {
  border-radius: 15px;
  border: 1px solid #EAEAEA;
  background: #FFF;
  padding: 30px;
  margin-bottom: 30px;
}
.results__header {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.results__header div:nth-child(1) h2 {
  font-weight: 25px;
  font-weight: 800;
  font-style: italic;
  color: #7c63ec;
  font-family: 'Raleway', sans-serif;
  margin: 0;
}
.results__header div:nth-child(1) p {
  font-weight: 17px;
  font-weight: 500;
  font-style: italic;
  color: #000;
  font-family: 'Raleway', sans-serif;
  margin: 0;
}
.results__header div:nth-child(2) p {
  font-weight: 17px;
  font-weight: 500;
  font-style: italic;
  color: #000;
  font-family: 'Raleway', sans-serif;
  text-align: right;
  margin: 0;
}
.results__header div:nth-child(2) h3 {
  font-weight: 25px;
  font-weight: 800;
  font-style: italic;
  color: #FFBC0F;
  font-family: 'Raleway', sans-serif;
  margin: 0;
}
.numbers {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 12px;
  align-items: center;
}
.number {
  width: 40px;
  height: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #333;
  color: #FFF;
  font-weight: 700;
  font-size: 17px;
  font-family: sans-serif;
  border-radius: 100px;
}
</style>