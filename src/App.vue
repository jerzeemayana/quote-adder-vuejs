<template>
<div class="container">
<app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
<app-new-quote @quoteAdded="newQuote"></app-new-quote>
<app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
<div class="row">
  <div class="col-sm-12 text-center">
   <div class="alert alert-info">info: Click on a Quote to Delete it!</div>

  </div>
</div>
</div>
</template>


<script>
import QuoteGrid from './assets/components/QuoteGrid.vue';
import NewQuote from './assets/components/NewQuote.vue';
import Header from './assets/components/Header.vue';
export default {
  data: function (){
    return {
      quotes: [
        'just a quote to see something'
      ],
      maxQuotes: 18
    }
  },
  methods: {
    newQuote(quote){
      if(this.quotes.length >= this.maxQuotes){
        return alert('plese delete quotes first')
      }
      this.quotes.push(quote);
    },
    deleteQuote(index){
      this.quotes.splice(index, 1);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  }
}

</script>

