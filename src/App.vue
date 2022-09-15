<template>
  <h1>IronContacts</h1>
  <table>
    <thead>
      <th>Picture</th>
      <th>Name</th>
      <th>Popularity</th>
      <th>Won Oscar</th>
      <th>Won Emmy</th>
    </thead>
    <tbody>
      <tr v-for="person in contacts" :key="person.id">
        <td>
          <img :src="person.pictureUrl" :alt="`${person.name} profile image`" />
        </td>
        <td>{{ person.name }}</td>
        <td>{{ person.popularity.toFixed(2) }}</td>
        <td v-if="person.wonOscar">🏆</td>
        <td v-else>&#32;</td>
        <td v-if="person.wonEmmy">🏆</td>
        <td v-else>&#32;</td>
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
