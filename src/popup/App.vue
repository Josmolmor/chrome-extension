<template>
  <div class="extension">
    <img class="landing" v-bind:src="img" alt="altru" />
    <h1 class="heading">WIP</h1>
    <ul id="example-1">
      <li v-for="item in clientList" :key="item.id">
        {{ item.id }}
      </li>
    </ul>
  </div>
</template>

<script>
// const browser = require('webextension-polyfill');
const APIURL = process.env.VUE_APP_API_URL;
const axios = require('axios');

export default {
  data() {
    return {};
  },

  computed: {
    clientList() {
      return axios.get(`${APIURL}users/list_clients?email=${process.env.VUE_APP_DEV_USER_EMAIL}`);
    },
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
.extension {
  // font-family: 'BasisGrotesquePro', serif;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-width: 15rem;
  padding: 1rem 1rem 2rem;
}
.landing {
  display: block;
}
.heading {
  text-align: center;
}
</style>
