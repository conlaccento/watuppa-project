<template>
  <h3>Ordini di {{ userEmail }} <br><small>negli ultimi 30 giorni</small></h3>
  <ul v-if="orders.length > 0">
    <li
        v-for="order in orders"
        :key="order.order_id">
        Ordine {{ order.order_id }} <br><small>{{ order.products }}</small>
    </li>
  </ul>
  <p v-else>Nessun ordine associato all'email inserita</p>
</template>

<script>
export default {
  name: 'SearchForm',
  data() {
    return {
      email: undefined
    }
  },
  props: {
    orders: Array,
    userEmail: String
  },
  methods: {
    handleSubmit(e) {
      this.$emit( 'submit', e )
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    font-size: 1.2rem;
    margin-bottom: 1rem;
  }

  ul {
    padding-left: 1rem;
  }
</style>
