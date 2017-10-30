<template>
  <v-app>
    <v-toolbar fixed app>
      <v-toolbar-title>My application</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn flat to="/dashboard">
          Dashboard
        </v-btn>
        <v-btn flat v-if="!$root.user" to="/login">
          Login
        </v-btn>
        <v-btn flat v-if="!$root.user" to="/signup">
          Signup
        </v-btn>
        <v-btn flat @click.prevent="logout" v-if="$root.user">
          Logout
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-content>
    <v-footer>
      Footer content
    </v-footer>
  </v-app>
</template>

<script>
import { logout } from "@/api/auth";
export default {
  name: "app",
  methods: {
    logout() {
      logout(this.$root);
      this.$router.push("/");
    }
  }
};
</script>

