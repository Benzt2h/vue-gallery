<template>
  <v-container class="imagelist">
    <v-row fluid justify="space-around">
      <v-col cols="12">
        <v-row align="center" justify="center">
          <router-link
            :to="{ name: 'Home' }"
            class="text-link display-1 text-center"
          >
            Back
          </router-link>
        </v-row>
      </v-col>
      <v-col cols="5" v-for="image in imageList" :key="image.id">
        <a :href="image.url" target="_blank">
          <v-img
            :alt="image.title"
            :src="image.thumbnailUrl"
            aspect-ratio="2"
          ></v-img>
        </a>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  name: "imagelist",
  data() {
    return {
      imageList: []
    };
  },
  mounted() {
    axios
      .get(
        `https://jsonplaceholder.typicode.com/photos?albumId=${this.$route.params.id}`
      )
      .then(res => {
        this.imageList = res.data;
      });
  }
};
</script>
