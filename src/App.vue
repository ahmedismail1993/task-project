<template>
  <div id="app">
    <CurrencyForm />
  </div>
</template>


<script>
export default {
  name: 'app',
  components: {
    CurrencyForm: () => import('@/components/CurrencyForm')
  }
};
</script>

<style >
#app {
  background-color: #fff;
}
* {
  box-sizing: border-box;
}
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
</style>