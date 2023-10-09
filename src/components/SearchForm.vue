<template>
  <form @submit.prevent="handleSubmit">
    <label for="email" class="screen-reader-text">Indirizzo e-mail: </label>
    <input v-model="email" type="email" name="email" id="email" placeholder="name@example.com" required />
    <input type="submit" value="Cerca" />
  </form>
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
    // msg: String
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
  input {
    font-family: "Allerta Stencil", Georgia, "Times New Roman", Times, serif;
    display: block;
    box-sizing: border-box;
    width: 100%;
    background-color: white;
    border-radius: 0;
    border: none;
    font-size: 1rem;
    padding: .8em;
    margin-bottom: .8em;
    line-height: 2;
    box-shadow: none;
    height: auto;
  }

  input[type="submit"] {
    background-color: #007bb5;
    border-color: #007bb5;
    box-shadow: none;
    color: #fff;
    font-size: 1.2rem;
    padding: .5em 1.5em;
    line-height: 1.75;
    width: auto;
  }
</style>
