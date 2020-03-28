<template>
    <div class="q-pa-md row items-start q-gutter-md" >
     <q-card class="my-card col-xs-11 col-md-3">
        <q-card-section>
          <div class="text-h6">{{coins ? coins.USD.name : ""}}</div>
        </q-card-section>
        <q-card-section class="q-pt-none">
          Variação do {{coins ? coins.USD.name : ""}}
        </q-card-section>
        <q-separator inset />
        <div class="row">
          <div class="col-6">
            <q-card-section>
              <small> Máx </small><br />
              <label class="custom-label text-red"> R$ {{coins ? formatPrice(coins.USD.high) : ""}} </label>
            </q-card-section>
          </div>
          <div class="col-6">
            <q-card-section>
              <small> Min </small><br />
              <label class="custom-label text-indigo"> R$ {{coins ? formatPrice(coins.USD.low) : ""}} </label>
            </q-card-section>
          </div>
        </div>
      </q-card>

      <!-- Dolar turismo -->
      <q-card class="my-card col-xs-11 col-md-3">
        <q-card-section>
          <div class="text-h6">{{coins ? coins.USDT.name : ""}}</div>
        </q-card-section>
        <q-card-section class="q-pt-none">
          Variação do {{coins ? coins.USDT.name : ""}}
        </q-card-section>
        <q-separator inset />
         <div class="row">
          <div class="col-6">
            <q-card-section>
              <small> Máx </small><br />
              <label class="custom-label text-red"> R$ {{coins ? formatPrice(coins.USDT.high) : ""}} </label>
            </q-card-section>
          </div>
          <div class="col-6">
            <q-card-section>
              <small> Min </small><br />
              <label class="custom-label text-indigo"> R$ {{coins ? formatPrice(coins.USDT.low) : ""}} </label>
            </q-card-section>
          </div>
        </div>
      </q-card>

      <!-- Euro -->
      <q-card class="my-card col-xs-11 col-md-3">
        <q-card-section>
          <div class="text-h6">{{coins ? coins.EUR.name : ""}}</div>
        </q-card-section>
        <q-card-section class="q-pt-none">
          Variação do {{coins ? coins.EUR.name : ""}}
        </q-card-section>
        <q-separator inset />
         <div class="row">
          <div class="col-6">
            <q-card-section>
              <small> Máx </small> <br />
              <label class="custom-label text-red"> R$ {{coins ? formatPrice(coins.EUR.high) : ""}} </label>
            </q-card-section>
          </div>
          <div class="col-6">
            <q-card-section>
              <small> Min </small><br />
              <label class="custom-label text-indigo"> R$ {{coins ? formatPrice(coins.EUR.low) : ""}} </label>
            </q-card-section>
          </div>
        </div>
      </q-card>

      <!-- Bitecoin -->
      <q-card class="my-card col-xs-11 col-md-3">
        <q-card-section>
          <div class="text-h6">{{coins ? coins.BTC.name : ""}}</div>
        </q-card-section>
        <q-card-section class="q-pt-none">
          Variação do {{coins ? coins.BTC.name : ""}}
        </q-card-section>
        <q-separator inset />
         <div class="row">
          <div class="col-6">
            <q-card-section>
              <small> Máx </small> <br />
              <label class="custom-label text-red"> R$ {{coins ? formatPrice(coins.BTC.high) : ""}} </label>
            </q-card-section>
          </div>
          <div class="col-6">
            <q-card-section>
              <small> Min </small><br />
              <label class="custom-label text-indigo"> R$ {{coins ? formatPrice(coins.BTC.low) : ""}} </label>
            </q-card-section>
          </div>
        </div>
      </q-card>

      <!-- Yene Japônes -->
      <q-card class="my-card col-xs-11 col-md-3">
        <q-card-section>
          <div class="text-h6">{{coins ? coins.JPY.name : ""}}</div>
        </q-card-section>
        <q-card-section class="q-pt-none">
          Variação do {{coins ? coins.JPY.name : ""}}
        </q-card-section>
        <q-separator inset />
         <div class="row">
          <div class="col-6">
            <q-card-section>
              <small> Máx </small> <br />
              <label class="custom-label text-red"> R$ {{coins ? coins.JPY.high : ""}} </label>
            </q-card-section>
          </div>
          <div class="col-6">
            <q-card-section>
              <small> Min </small><br />
              <label class="custom-label text-indigo"> R$ {{coins ? coins.JPY.low : ""}} </label>
            </q-card-section>
          </div>
        </div>
      </q-card>
    </div>
</template>
<style scoped>
  .custom-label{
    font-size: 25px;
  };

</style>
<script>
import axios from 'axios';
export default {
  name: 'PageIndex',
  data () {
    return {
      coins: null,
      coin_select: null
    }
  },
  methods: {
    getValueCoins: function(){
      this.$q.loading.show({
        delay: 100 // ms
      })
      let vm = this
      axios.get('https://economia.awesomeapi.com.br/json/all')
      .then(function (response) {
        vm.coins = response.data
        vm.$q.loading.hide()
      })
      .catch(function (error) {

      });
    },
    formatPrice(value) {
        let val = (value/1).toFixed(2).replace('.', ',')
        return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".")
    }
  },
  beforeCreate() {
  },
  created () {
    this.getValueCoins()
  }
}
</script>
