<template>
  <v-container class="home">
    <v-row>
      <v-col cols="3" v-for="album in albums" :key="album.id">
        <v-card class="mx-auto" max-width="344" outlined>
          <v-list-item three-line>
            <v-list-item-content>
              <div class="overline mb-4"></div>
              <v-list-item-subtitle>{{ album.title }} </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <v-card-actions>
            <router-link
              :to="{ name: 'ImageList', params: { id: album.id } }"
              class="text-link mr-5"
            >
              View
            </router-link>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      albums: []
    };
  },
  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/albums").then(res => {
      this.albums = res.data;
    });
  }
};
</script>
