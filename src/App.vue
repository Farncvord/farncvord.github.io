<template>
  <div>
    <button @click="increment(click_increment)">
      {{money}}
    </button>
    <button @click="upgrade(click_increment)">
      {{value(click_increment)}}
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      money: 0,
      click_increment: {
        level: 1,
        base_value: 1,
        increment_value: 1,
        base_price: 10,
        increment_price: 2
      }
    }
  },

  mounted() {

  },

  methods: {
    increment(param) {
      this.money += this.value(param);
    },

    upgrade(param) {
      let price = param.base_price + (param.level - 1) * param.increment_price;

      if( this.money >= price) {
        this.money -= price;

        param.level++;
      }
    },

    value(param) {
      return param.base_value + (param.level - 1) * param.increment_value;
    }
  }
}

</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
