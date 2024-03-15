<template>
  <MainHeader />
  <router-view />
  <MainFooter />
  <a href="#bodyContent" class="back-to-top">Voltar ao topo</a>
</template>

<script>
import MainHeader from '@/components/MainHeader.vue'
import MainFooter from '@/components/MainFooter.vue'
export default {
  components: {
    MainHeader,
    MainFooter
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Raleway:ital,wght@0,100..900;1,100..900&display=swap');
a.back-to-top {
  text-align: center;
  margin: 30px auto;
  display: table;
  font-family: 'Raleway', sans-serif;
  font-size: 17px;
  font-weight: 500;
}
</style>