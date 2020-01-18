<template>
  <div class="container">
    <div class="col">
      <h1 style="text-align:center">Sample Table</h1>
      <button @click="loadData()">Load Data</button>
      <table class="d-flex flex-column">
        <tr class="d-flex">
          <th class="col-1">id</th>
          <th class="col-5">name</th>
          <th class="col-6">url</th>
        </tr>
        <tr class="d-flex" v-for="site in sites" :key="site.id">
          <th class="col-1" scope="row">{{site.id}}</th>
          <td class="col-5">{{site.name}}</td>
          <td class="col-6">{{site.url}}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import Logo from "~/components/Logo.vue";
import axios from "axios";

export default {
  components: {},
  data() {
    return {
      sites: []
    };
  },
  created() {},
  methods: {
    async loadData() {
      const config = {
        headers: {
          Accept: "application/json"
        }
      };
      try {
        const res = await axios.get(
          "https://aimtell.com/files/sites.json",
          config
        );
        this.sites = res.data.sites;
      } catch (err) {
        console.log(err);
      }
    }
  },
  head() {
    return {
      title: `Push Pros`,
      meta: [
        {
          hid: "pushpros",
          name: "pushpros",
          content: "Pushing them pros!"
        }
      ]
    };
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: left;
}


</style>
