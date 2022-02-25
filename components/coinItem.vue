<template>
  <div class="coin" id="list-item">
    <div class="data-column"><img :src="coin.image.small" /></div>
    <div class="data-column">{{ coin.symbol.toUpperCase() }}</div>
    <div class="data-column">{{ usdToBTC }} $</div>
    <div class="data-column"># {{ coin.market_cap_rank }}</div>
  </div>
</template>

<script>
export default {
  name: "coin-item",
  props: ["coin"],
  data() {
    return {};
  },
  computed: {
    usdToBTC: function () {
      for (const ticker of this.coin.tickers) {
        if (
          ticker.base === this.coin.symbol.toUpperCase() &&
          ticker.target === "USD"
        ) {
          return ticker.last;
        }
      }
      return "N/A";
    },
  },
};
</script>

<style scoped>
.coin {
  background: #85144b;
  display: inline-flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  padding-right: 2rem;
  margin-bottom: 0.2rem;
  border-bottom: 1px solid white;
  border: 3px solid plum;
  border-radius: 25px;
  box-shadow: 0 0 50px rgb(106, 29, 151);
  min-width: 30rem;
  transition: 0.15s;
}
.coin:hover {
  transform: rotate(5deg);
}
.data-column {
  font-size: 11px;
  font-size: 1.5rem;
  color: white;
}
</style>
