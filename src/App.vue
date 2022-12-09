<template>
  <h1>IronContacts</h1>
  <button @click="getRandomContact">Add Random Contact</button>
  <button @click="sortByPopularity">Sort by Popularity</button>
  <button @click="sortByName">Sort by Name</button>
  <table>
    <thead>
      <th>Picture</th>
      <th>Name</th>
      <th>Popularity</th>
      <th>Won Oscar</th>
      <th>Won Emmy</th>
      <th>Actions</th>
    </thead>
    <tbody>
      <tr v-for="contact in currentContacts" :key="contact.id">
        <td>
          <img
            :src="contact.pictureUrl"
            :alt="`${contact.name} profile image`"
          />
        </td>
        <td>{{ contact.name }}</td>
        <td>{{ contact.popularity.toFixed(2) }}</td>
        <td v-if="contact.wonOscar">🏆</td>
        <td v-else>&#32;</td>
        <td v-if="contact.wonEmmy">🏆</td>
        <td v-else>&#32;</td>
        <td><button @click="deleteContact(contact.id)">Delete</button></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import contacts from "./contacts.json";

export default {
  data() {
    return {
      contacts,
      currentContacts: [...contacts].slice(0, 5),
      maxContacts: contacts.length,
    };
  },
  methods: {
    getRandomContact() {
      let i = Math.floor(Math.random() * this.maxContacts);
      this.addRandomContact(this.contacts[i]);
    },
    addRandomContact(randomContact) {
      this.currentContacts.find((contact) => contact.id === randomContact.id)
        ? this.getRandomContact()
        : this.currentContacts.push(randomContact);
    },
    deleteContact(contactID) {
      this.currentContacts = this.currentContacts.filter(
        (contact) => contact.id !== contactID
      );
    },
    sortByPopularity() {
      this.currentContacts.sort((a, b) =>
        a.popularity > b.popularity ? -1 : b.popularity > a.popularity ? 1 : 0
      );
    },
    sortByName() {
      this.currentContacts.sort((a, b) =>
        a.name > b.name ? 1 : b.name > a.name ? -1 : 0
      );
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  margin-bottom: 4rem;
}

img {
  max-width: 100px;
}

table {
  margin: auto;
}

th {
  padding: 1rem 2rem;
}
</style>
