<template>
<h1>{{ contacts }}</h1>

  <table>
    <tr>
      <th>IronContacts</th>
    </tr>
    <tr>
      <th>Picture</th>
      <th>Name</th>
      <th>Popularity</th>
      <th>Won Oscar</th>
      <th>Won Emmy</th>
    </tr>
    <tr v-for="contact in contacts">
      <td><img class="smallPicture" :src="contact.pictureUrl" /></td>
      <td>{{ contact.name }}</td>
      <td>{{ contact.popularity }}</td>
      <td v-if="contact.wonOscar">🏆</td>
      <td v-else>    </td>
      <td v-if="contact.wonEmmy">🏆</td>
    </tr>
  </table>
  <button @click="_addRandomContact">Add Contact</button>
</template>

<script>
import { computed } from "@vue/reactivity";
import contactsJson from "./contacts.json";

export default {
  name: 'App',
  data() {
    return {
      dataContact: contactsJson,
      contacts: [],
      contactsNotShowed: [],
      numberOfContacts: 5,
    }
  },
  created() {
   this._firstFiveContact();
    console.log(this.dataContact);
    console.log(this.unShowedContact);
    console.log(this.showContact);

  },
  methods: {
     _firstFiveContact() {
      const sizeArr = this.dataContact.length;
      this.contacts = this.dataContact.slice(0,this.numberOfContacts)
      this.contactsNotShowed = this.dataContact.slice(this.numberOfContacts,sizeArr)

      console.log(sizeArr);
      console.log(this.contacts);
      console.log(this.contactsNotShowed)
    },

    _addRandomContact() {
      //const randomContact = Math.floor(Math.random())
     this.contacts.push(this.contactsNotShowed[0]);
     this.contactsNotShowed.shift()

     console.log(this.contacts);
     console.log(this.contactsNotShowed);

    }

  },
  computed: {
    /*showContact(){
      return this.dataContact.slice(0,this.numberOfContacts)
    },
    unShowedContact(){
      return this.dataContact.slice(this.numberOfContacts,this.dataContact.length)
    }*/

  }
}

</script>

<style scoped>
.smallPicture{
  width: 50px;
}

</style>
