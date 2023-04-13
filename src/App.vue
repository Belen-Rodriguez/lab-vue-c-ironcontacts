<template>
  <h1>{{ contactS }}</h1>
  <h1>Hola</h1>
</template>

<script>
import contacts from "./contacts.json";

export default {
  name: 'App',
  data() {
    return {
      contactS: contacts
    }
  },

  methods: {
    _firstFiveContact() {
      this.contactS = this.contacts
    }
  }
}

</script>

<style>

</style>
