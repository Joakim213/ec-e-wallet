<template>
  <div>
    <Top
      :title="title"
      :subTitle="subTitle"/>
    <div class="center-card">
        <Card :card="cardInfo"/>
    </div>
    <div class="center-object">
        <CardForm @sendCardInfo="giveValue"></CardForm>
    <a v-on:click="giveCard" class="cta">add card</a>
    </div>
  </div>
</template>

<script>
import CardForm from '@/components/CardForm'
import Top from '@/components/Top'
import Card from "@/components/Card";
export default {
  name: 'AddCard',
  components: {
    Top,
    CardForm,
    Card
  },
  data() {
    return {
      title: 'ADD A NEW CARD',
      subTitle: 'NEW CARD',
      cardInfo: {},
    }
  },
  methods: {
    giveValue(newCard){
      this.cardInfo= {
        cardNumber: newCard.cardNumber,
        name: newCard.name,
        expireMonth: newCard.expireMonth,
        expireYear: newCard.expireYear,
        currentYear: newCard.currentYear,
        vendor: newCard.vendor,
        id: newCard.id,
      }
    },
    giveCard(){
        this.$root.savedCards.push(this.cardInfo)
        this.$router.push("/")
    }
  }
}
</script>

<style scoped>
a.cta {
  align-items: center;
  height: 4rem;
  font-size: 1.2rem;
  text-transform: uppercase;
  font-weight: 700;
  text-decoration: none;
  color: #000;
  border: .125rem solid #000;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  border-radius: .5rem;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -ms-flex-align: center;
  margin: 2rem 0
}
a.cta:hover {
  background: #000;
  color: #ddd
}
a.cta:active {
  background: #000;
  color: #fff
}
</style>
