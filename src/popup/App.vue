<template>
  <div class="extension">
    <img class="landing" v-bind:src="img" alt="altru" />
    <RippleLoader v-if="clients.length <= 0 || videos.length <= 0" />
    <ul id="example-1">
      <li v-for="client in orderedClients" :key="client.id">{{ client.id }} - {{ client.name }}</li>
    </ul>
    <img class="video-thumbnail" v-for="video in videos.data" :key="video.id" :src="video.gif_url" alt="" />
  </div>
</template>

<script>
// const browser = require('webextension-polyfill');
// const APIURL = process.env.VUE_APP_API_URL;
import _ from 'lodash';
import RippleLoader from '../components/Loader/index';

const axios = require('axios');

export default {
  components: { RippleLoader },
  data() {
    return {
      clients: [],
      videos: [],
      // eslint-disable-next-line global-require
      img: 'https://assets.website-files.com/5d71246584d80240ec1470f0/5d71246584d80278e914713b_logo.svg',
    };
  },
  computed: {
    orderedClients() {
      return _.orderBy(this.clients.data, 'id');
    },
  },
  methods: {},
  mounted() {
    axios
      .get(`https://api-staging.altrulabs.com/api/v1/users/list_clients?email=1polidoro@rallyapps.com`)
      .then(response => {
        this.clients = response.data;
      })
      .catch(error => console.log(error));

    axios
      .get(`https://api-staging.altrulabs.com/api/v1/answers?client_id=9&page=1&per_page=20&q[status_in]=approved&order_by=-recorded_at&q[hint_match_gt]=0`)
      .then(response => {
        this.videos = response.data;
      })
      .catch(error => console.log(error));
  },
};
</script>

<style lang="scss" scoped>
.extension {
  // font-family: 'BasisGrotesquePro', serif;
  display: flex;
  flex-direction: column;
  min-width: 15rem;
  padding: 1rem 1rem 2rem;
}
.landing {
  display: block;
}
.heading {
  text-align: center;
}
.video-thumbnail {
  max-width: 100%;
  object-fit: cover;
}
</style>
