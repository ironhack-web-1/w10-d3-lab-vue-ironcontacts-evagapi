<template>
  <h1>IronContacts</h1>
  <table>
    <thead>
      <th>Picture</th>
      <th>Name</th>
      <th>Popularity</th>
    </thead>
    <tbody>
      <tr v-for="person in contacts" :key="person.id">
        <td>
          <img :src="person.pictureUrl" :alt="`${person.name} profile image`" />
        </td>
        <td>{{ person.name }}</td>
        <td>{{ person.popularity.toFixed(2) }}</td>
      </tr>
    </tbody>
  </table>
  <!-- <ul>
    <li v-for="person in contacts">{{ person.name }}</li>
  </ul> -->
</template>

<script>
import contacts from "./contacts.json";

export default {
  data() {
    return {
      contacts,
    };
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

img {
  max-width: 100px;
}

table {
  margin: auto;
}
</style>
