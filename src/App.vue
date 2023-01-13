<script>
import axios from 'axios';

import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'

export default {
  components: {
    AppHeader,
    AppMain
  },

  data() {
    return {
      apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0",
      cardList: [],
    }
  },

  methods: {
    getCard() {
      axios.get(this.apiUrl, {
        params: {
          //page: page
        }
      })
        .then((response) => {
          console.log(response.data.data);
          this.cardList = response.data.data;
        })
        .catch(function (error) {
          console.warn(error);
        });
    },
  },

  created() {
    this.getCard();
  },
}
</script>

<template>
  <AppHeader />
  <AppMain :cards="cardList" />
</template>

<style lang="scss">
@use './styles/general.scss' as *;
@use './styles/partials/variables' as *;
</style>

