<template>
  <main class="container">
    <section class="container__group container__group--dollarSign container__group--dollarSign--1">
      <label for="price">Purchase price</label>
      <input id="price" v-model="form.price" />
      <select v-model="form.currency" class="container__selectDown">
        <option :value="form.currency">{{form.currency}}</option>
      </select>
    </section>

    <section class="container__group">
      <div class="container__group--wrapper">
        <label for="plot_size">Plot size</label>
        <input id="plot_size" v-model="form.plotSize" />
        <span class="total-percent">
          | m
          <span class="squared">2</span>
        </span>
      </div>
    </section>

    <section class="container__group">
      <div class="container__group--wrapper">
        <label for="yearOfConstruction">Year of construction</label>
        <input id="yearOfConstruction" v-model="form.yearOfConstruction" />
      </div>
    </section>
    <section class="container__group">
      <div class="container__group--wrapper">
        <label for="netRentTotal">Net rent total (p.a.)</label>
        <input id="netRentTotal" v-model="form.netRentTotal" />
        <span class="total-percent">| $ / p.a.</span>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: 'currencyForm',
  data() {
    return {
      form: {
        price: '',
        plotSize: '',
        yearOfConstruction: '',
        netRentTotal: '',
        currency: ''
      }
    };
  },
  created() {
    this.fetcData();
  },
  methods: {
    async fetcData() {
      try {
        const response = await fetch('https://server.offmade.io/code-challenge');
        const data = await response.json();
        this.form = data;
        console.log(data);
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>

<style lang="scss" >
.container {
  padding: 20px;
  background: #f8f8f8;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-wrap: wrap;
  width: 80vw;
  height: 80vh;
  margin: 20px auto;

  &__group {
    width: 40%;
    position: relative;

    &--dollarSign {
      &::after {
        content: '$';
        position: absolute;
        right: 5px;
        top: 50%;
        line-height: 40px;
        width: 100px;
        height: 100px;
      }
    }

    input {
      width: 100%;
      padding: 30px;
      outline: none;
      margin-top: 10px;
      box-shadow: 0 4px 10px #efefef;
      border-radius: 8px;
      background: #fff;
      border: none;
    }
    #netRentTotal {
      color: #ccc;
    }
    label {
      color: #ababab;
    }
    &--wrapper {
      width: 50%;
      position: relative;
    }
  }
  &__selectDown {
    position: absolute;
    top: 50%;
    right: 15px;
    padding: 11px;
    width: 76px;
    border: none;
    background-color: #fff;
    border-left: 1px solid rgb(230, 230, 230);
    border-radius: 2px;
    outline: none;
  }
  .total-percent {
    position: absolute;
    top: 55%;
    right: 30px;
    color: #9e9e9e;
  }
  .squared {
    font-size: 12px;
    position: absolute;
  }
}
</style>