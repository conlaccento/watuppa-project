<template>
  <div class="box">
    <div class="box__header">
      <h2>Cerca ordini</h2>
    </div>
    <div class="box__body">
      <div class="search-form">
        <SearchForm @submit="handleSubmit" />
      </div>
      <hr v-if="userEmail != undefined">
      <div v-if="userEmail != undefined" class="search-results">
        <OrdersList :userEmail="userEmail" :orders="orders" />
      </div>
    </div>
  </div>
</template>

<script>
import OrdersList from './components/OrdersList.vue';
import SearchForm from './components/SearchForm.vue';

export default {
  name: 'App',
  components: {
    SearchForm,
    OrdersList
},
  data() {
    return {
      userEmail: undefined,
      orders: []
    }
  },
  methods: {
    handleSubmit(e) {
      const email = e.target.elements.email.value
      this.userEmail = email
      fetch('http://localhost:8888/watuppa-backend/api.php?email=' + this.userEmail)
        .then(res => res.json())
        .then(data => this.orders = data)
        .catch(err => console.log(err.message))
    }
  }
}
</script>

<style>
@import url('https://db.onlinewebfonts.com/c/f516503a27e45e97846067c3834cb354?family=Lyon+Text+OSF+Web+Regular+Regular');
@import url('https://fonts.cdnfonts.com/css/allerta-stencil');
* {
  margin: 0;
  padding: 0;
}
body {
  font-family: "Lyon Text OSF Web", Georgia, "Times New Roman", Times, serif;
  display: grid;
  place-content: center;
  min-height: 100vh;
  color: #000;
  font-size: 1rem;
}

h1, h2, h3 {
  font-family: "Allerta Stencil", Georgia, "Times New Roman", Times, serif;
}

/* Text meant only for screen readers. */
.screen-reader-text {
  border: 0;
  clip: rect(1px, 1px, 1px, 1px);
  clip-path: inset(50%);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
  word-wrap: normal !important;
}

.box {
  width: 470px;
}

.box__header {
  padding: 0 1.5rem;
  background-color: #002440;
  color: #fff;
}

.box__header h2 {
  font-size: 1.5rem;
  line-height: 2;
}

.box__body {
  padding: 1.5rem;
  background-color: #f5f4f4;
  border-bottom: 1px solid #ddd;
  border-left: 1px solid #ddd;
  border-right: 1px solid #ddd;
}

hr {
  margin: 1rem 0;
  border: 0;
  border-top: 1px solid #c8c8c8;
}
</style>
