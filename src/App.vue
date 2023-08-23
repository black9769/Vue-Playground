<template>
  <v-layout class="rounded rounded-md">
    <v-navigation-drawer>
      <v-list>
        <v-list-item title="Navigation drawer">
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar title="Application bar"></v-app-bar>

    <v-main class="d-flex align-center justify-center" style="min-height: 300px;">
      {{name}}
      {{env}}
    </v-main>
  </v-layout>
</template>

<script>
import axios from "axios";

export default {
  name: "main",
  mounted() {
    this.getUserName()
  },
  data () {
    return {
      name,
      env: import.meta.env.VITE_TEST
    };
  },

  methods: {
    getUserName() {
      axios.get("api/test")
          .then((res) => this.name = res.data)
          .catch((err) => console.log(err))
    }
  }
}
</script>