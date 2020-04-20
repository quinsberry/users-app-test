<template>
  <v-app md>
    <v-navigation-drawer app>
      <Sidebar v-bind:users="users" @select-user="setSelectedUser" v-bind:loading="loading" />
    </v-navigation-drawer>

    <v-app-bar app>
      <Header />
    </v-app-bar>

    <v-content>
      <Content v-bind:user="selectedUser" />
    </v-content>
  </v-app>
</template>

<script>
import Header from "./components/Header";
import Sidebar from "./components/Sidebar";
import Content from "./components/Content";

export default {
  name: "App",

  components: {
    Header,
    Sidebar,
    Content
  },
  mounted() {
    fetch("https://randomuser.me/api/?results=20")
      .then(res => res.json())
      .then(res => {
        this.users = res.results;
        this.loading = false;
      });
  },
  data: () => ({
    users: [],
    selectedUser: null,
    loading: true
  }),
  methods: {
    setSelectedUser(selectedUser) {
      this.selectedUser = selectedUser;
    }
  }
};
</script>

