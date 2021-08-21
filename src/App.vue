<template>
  <button @click="getList">Get list</button>
  <h2>Member list</h2>
  <table>
    <tr>
      <th>Name</th>
      <th>Username</th>
      <th>Address</th>
      <th>Email</th>
      <th>Phone</th>
      <th>Roles</th>
    </tr>
    <tr v-for="user in list" :key="user">
      <td>{{ user["name"] }}</td>
      <td>{{ user["username"] }}</td>
      <td>{{ user["address"] }}</td>
      <td>{{ user["email"] }}</td>
      <td>{{ user["phone"] }}</td>
      <td>{{ user["roles"].join(",") }}</td>
    </tr>
  </table>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      list: "",
    };
  },
  methods: {
    async getList() {
      try {
        const res = await axios.post("http://localhost:4002/genericgraphql", {
          query:
            "query {allUsers {users {name username address email phone roles {role}}}}",
        });
        this.list = res.data.data.allUsers.users;
      } catch (e) {
        console.log("err", e);
      }
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
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td,
th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
