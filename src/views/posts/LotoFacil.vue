<template>
    <div class="container top70" id="bodyContent">
        <article v-if="data">
            <h1>Sorteio Histórico da {{ data.tituloModalidade }}: Prêmio de {{ data.valorSorteado }} é Conquistado no Concurso {{ data.concurso }}</h1>
            <figure>
                <img src="@/assets/posts/lotofacil.webp" class="post-banner">
            </figure>
            <p>
                Uma noite memorável para os amantes da {{ data.tituloModalidade }}! O Espaço da Sorte, localizado em São Paulo, SP, foi palco do aguardado sorteio do Concurso {{ data.concurso }} da {{ data.tituloModalidade }}, que não decepcionou os participantes ávidos por uma chance
                de mudar de vida. O clima de expectativa pairava no ar enquanto os números eram sorteados, e a emoção atingiu seu ápice quando a combinação vencedora foi revelada. Para a surpresa e alegria de muitos, um único apostador conseguiu acertar todos os 15 números sorteados, garantindo assim o prêmio milionário de {{ data.valorSorteado }}.
            </p>
            <p>
                Esse feito não apenas reforça a popularidade e o apelo da {{ data.tituloModalidade }} entre os jogadores, mas também ressalta a importância de se manter a esperança e a persistência. Afinal, em um jogo baseado em probabilidades, a sorte pode sorrir para qualquer um a qualquer momento.
            </p>
            <p>
                O vencedor, cuja identidade ainda é desconhecida, certamente terá muitos planos para o prêmio conquistado. Seja para realizar sonhos pessoais, investir em projetos ou ajudar familiares e amigos, essa quantia significativa certamente fará diferença em sua vida e na vida daqueles ao seu redor.
            </p>
            <p>
                Enquanto isso, para os demais jogadores que não tiveram a mesma sorte neste sorteio, a {{ data.tituloModalidade }} continua sendo uma oportunidade única de tentar a sorte e quem sabe também alcançar seus objetivos. Com sorteios regulares e prêmios atrativos, o jogo oferece uma dose saudável de emoção e esperança a milhões de brasileiros.
            </p>
            <p>
                E assim, o Concurso {{ data.concurso }} da {{ data.tituloModalidade }} entra para a história como mais uma emocionante noite em que os números decidiram o destino de um sortudo ganhador. Enquanto aguardamos ansiosamente pelo próximo sorteio, resta aos jogadores continuarem apostando, sonhando e mantendo viva a esperança de que um dia a sorte possa bater à sua porta.
            </p>
        </article>
        <article id="placeholder" v-else>
            <h1></h1>
            <figure></figure>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
            <p></p>
        </article>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            data: [],
        }
    },
    async mounted() {
        try {
            const response = await axios.get('https://resultados-loterias-json.vercel.app/api/resultados')
            this.data = response.data.lotofacil
        } catch (error) {
            console.error(error)
        }
        window.scrollTo(0, 0);
    },
}
</script>

<style scoped>
@media screen and (max-width: 800px) {
    .top70 {
        margin-top: 75px;
    }
}
img.post-banner {
    width: 100%;
    min-height: auto;
    max-width: 640px;
    margin: 0 auto;
    display: table;
    
}
h1 {
    font-size: 25px;
    font-weight: 800;
    font-family: 'Raleway', sans-serif;
    color: #000;
    margin-bottom: 12px;
}

#placeholder h1 {
    width: 100%;
    height: 40px;
    border-radius: 5px;
    background: #EAEAEA;
    display: table;
}
#placeholder figure {
    width: 100%;
    height: 300px;
    background: #EAEAEA;
    display: table;
}
#placeholder p {
    width: 100%;
    height: 20px;
    display: table;
    background: #EAEAEA;
}
</style>