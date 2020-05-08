<template>
  <div id='card-search'>
    <input type="text" v-model=cardName>
    <button @click=getCard(cardName)>Make Call</button>
    <p>
      <img :src=imageUrl>
    </p>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'CardSearch',

  data () {
    return {
      cardName: '',
      imageUrl: ''
    };
  },

  methods: {
    getCard (cardName) {
      axios.get('http://localhost:8080/card/' + cardName).then(response => {
      this.card = response;
      this.imageUrl = this.card.data.imageUrl;
      });
    }
  }
  
}
</script>
<style scoped>
</style>
