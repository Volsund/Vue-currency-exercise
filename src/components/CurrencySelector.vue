<template>
  <div class="currency-selector">
    <div class="selected-currencies">
      <div
        class="single-selected-currency"
        v-for="selected in selectedItems"
        :key="selected.title"
      >
        {{ selected.title.toLowerCase() }}
        <span class="close" @click="deselect(selected)"></span>
      </div>
    </div>
    <div class="listed-currencies">
      <div
        class="single-currency"
        v-for="currency in currencies"
        :key="currency.title"
      >
        <label class="currency-name">
          <input
            class="checkbox"
            type="checkbox"
            v-model="currency.checked"
            :id="currency.title"
          />
          {{ currency.title }}
        </label>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CurrencySelector",
  data() {
    return {
      currencies: [
        { title: "EUR", checked: false },
        { title: "PLN", checked: false },
        { title: "DKK", checked: false },
        { title: "CZK", checked: false },
        { title: "GBP", checked: false },
        { title: "SEK", checked: false },
        { title: "USD", checked: false },
        { title: "RUB", checked: false },
      ],
    };
  },
  computed: {
    selectedItems() {
      return this.currencies.filter((curr) => curr.checked === true);
    },
  },
  methods: {
    deselect(toRemove) {
      toRemove.checked = false;
    },
  },
};
</script>

<style scoped>
.currency-selector {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 90%;
  max-width: 366px;
  border: 1px var(--border-color) solid;
  border-radius: 4px;
}

.selected-currencies,
.listed-currencies {
  width: 95%;
  margin: 10px auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
}

.single-currency,
.single-selected-currency {
  background-color: rgba(173, 158, 158, 0.87);
  margin: 5px;
  padding: 5px;
  font-size: 1.3rem;
  width: calc(33.3% - 10px);
}

@media screen and (max-width: 400px) {
  .single-currency,
  .single-selected-currency {
    width: calc(50% - 10px);
  }
}
@media screen and (max-width: 300px) {
  .single-currency,
  .single-selected-currency {
    width: calc(100% - 10px);
  }
}
.single-currency {
  border: 1px solid var(--border-color);
  color: rgb(34, 34, 94);
}

.single-selected-currency {
  border-radius: 4px;
  text-align: center;
  position: relative;
}

.close:after {
  content: "x";
  color: #fff;
  border-radius: 50%;
  border: 2px solid var(--accent-color);
  position: absolute;
  top: -5px;
  right: -5px;
  background-color: var(--accent-color);
  line-height: 0.8;
}

.close:hover:after {
  color: var(--accent-color);
  background-color: #fff;
  cursor: pointer;
}
</style>
