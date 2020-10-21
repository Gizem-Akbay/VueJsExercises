<template>
  <div> 
    <div class="container">
        <div class="row">
          <div :key="index" v-for="(card, index) in dup_rand_card" @click="turnCard(card)" class="col-md-3">
            <appCard                  
              :class="{'shadow' : cards.turn == true}"
              :card="card"
              :index="index">
            </appCard>
          </div>
        </div>
    </div>
  </div>
</template>
<script>
  import Card from "./Card";
  export default {
    components: {
      appCard: Card
    },
    data() {
      return {
        openedCards: [],
        dup_rand_card: [],
        cards: [
          {id: 1,turn:false,matched:false,image: "card-1.jpg", key:1},
          {id: 2,turn:false,matched:false,image: "card-2.jpg", key:2},
          {id: 3,turn:false,matched:false,image: "card-3.jpg", key:3},
          {id: 4,turn:false,matched:false,image: "card-4.jpg", key:4},
          {id: 5,turn:false,matched:false,image: "card-5.jpg", key:5},
          {id: 6,turn:false,matched:false,image: "card-6.png", key:6},
          {id: 7,turn:false,matched:false,image: "card-7.png", key:7},
          {id: 8,turn:false,matched:false,image: "card-8.png", key:8}
        ],
      }
    },
    mounted() {
      this.newGame();
    },
    methods: {
      newGame: function() {
        this.generateCards();
      },
      generateCards: function() {
        var cards = [];
        var cardId = 0;
        this.cards.forEach((card) => {
          for (var i = 0; i < 2; i++) {
            cardId += 1;
            cards.push({
              id: cardId,
              turn: false,
              matched: false,
              image: card.image,
              key: card.key
            });
          }
        });
        this.dup_rand_card = cards.sort(() => .5 - Math.random());
        console.log(this.dup_rand_card);
      },
      turnCard: function(card) {
        if (this.openedCards.length === 2 || card.matched) {
          return;
        }
        card.turn = true;
        this.openedCards.push(card);
        if (this.openedCards.length === 2) {
          setTimeout(() => {
            this.isMatch(this.openedCards);
          }, 500);
        } 
      },
      isMatch: function(openedCards) {
        if (openedCards[0].key === openedCards[1].key) {
          openedCards[0].turn = true;
          openedCards[0].matched = true;
          openedCards[1].matched = true;
          openedCards[1].turn = true;
        } else {
          this.dup_rand_card.forEach(card => {
            card.turn = false;
          });
        }
        this.openedCards = [];
      }
    }
  };
</script>
<style scoped>
  
  .container{
    margin-top: 60px;
  }
  .shadow{
    box-shadow: 0px 5px 48px #30969f!important;
    transition: box-shadow .5s;
  }
  .rotate-all-enter{}
  .rotate-all-enter-active{
    animation : rotate-all ease-in-out 2s forwards;
  }
  .rotate-all-leave{}
  .rotate-all-leave-active{}
  @keyframes rotate-all {
    from{
      transform: rotateY(0);
    }
    to{
      transform: rotateY(1080deg);
    }
  }
</style>

















