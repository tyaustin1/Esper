<template>
  <div id='card-search'>
    <b-form-textarea
      id="textarea"
      v-model="cardName"
      placeholder="Enter something..."
      rows="3"
      max-rows="6"
    ></b-form-textarea>
    <button @click=getCards(cardName)>Make Call</button>
   <img v-for="imageUrl in imageUrls" :src="imageUrl" :key="imageUrl"/>

  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'CardSearch',

  data () {
    return {
      cardName: '',
      imageUrl: '',
      imageUrls: []
    };
  },

  methods: {
    getCard (cardName) {
      axios.get('http://localhost:8080/card/' + cardName).then(response => {
      this.card = response;
      this.imageUrl = this.card.data.imageUrl;
      });
    },
    getCards (cardName) {
      let listOfCardNames = cardName.split('\n');
      const headers = {
  'Content-Type': 'application/json',
}
      axios({
        method: 'post',
        url: 'http://localhost:8080/cards',
        headers: headers,
        data: listOfCardNames
        })
        .then((response) => {
            //handle success
            console.log(response.data[0].imageUrl)
            let cardArray = response.data;
            console.log(cardArray);

            cardArray.forEach(element => {
              this.imageUrls.push(element.imageUrl)
            });
        })
        .catch(function (response) {
            //handle error
            console.log(response);
        });
    }
  }
  
}
</script>
<style scoped>
</style>
