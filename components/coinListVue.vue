<template>
  <div>
    <div id="list-item" v-for="coin in coins" :key="coin.id">
      <coinItem :coin="coin" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      coins: [],
      errors: [],
    };
  },
  async created() {
    try {
      const requests = [
        axios.get(`https://api.coingecko.com/api/v3/coins/bitcoin`),
        axios.get(`https://api.coingecko.com/api/v3/coins/ethereum`),
        axios.get(`https://api.coingecko.com/api/v3/coins/tether `),
        axios.get(`https://api.coingecko.com/api/v3/coins/solana `),
        axios.get(`https://api.coingecko.com/api/v3/coins/dogecoin `),
        axios.get(`https://api.coingecko.com/api/v3/coins/cardano `),
        axios.get(`https://api.coingecko.com/api/v3/coins/litecoin `),
        axios.get(`https://api.coingecko.com/api/v3/coins/polkadot `),
        axios.get(`https://api.coingecko.com/api/v3/coins/stellar `),
        axios.get(`https://api.coingecko.com/api/v3/coins/monero `),
        axios.get(`https://api.coingecko.com/api/v3/coins/shiba-inu `),
        axios.get(`https://api.coingecko.com/api/v3/coins/decentraland `),
      ];

      let responses = await axios.all(requests);
      responses.forEach((coin) => {
        this.coins.push(coin.data);
      });
    } catch (e) {
      this.errors.push(e);
    }
  },
};
</script>
