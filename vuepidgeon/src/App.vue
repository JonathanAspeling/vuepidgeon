<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div>Meow</div>
  <p v-for="record in this.shop_records">{{ record }}</p>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  props: [],
  data() {
    return {
      request_url:
        "https://spreadsheets.google.com/feeds/list/1tdTxwv8j_De1VTbBhYMwC0B3B6_ZdIBgBVOdkxE0FJI/1/public/values?alt=json",
      shop_records: [],
    };
  },
  components: {},
  methods: {},
  mounted() {
    let shop_records_mnt = [];
    function parse_data(json_payload) {
      json_payload.forEach((value) => {
        var temp_record = {
          shop_item: value.gsx$winkelitem.$t,
          shop_price: value.gsx$prys.$t,
          dep: value.gsx$departement.$t,
        };
        this.shop_records.push({
          item: temp_record.shop_item,
          price: temp_record.shop_price,
          dep: temp_record.dep,
        });
      });
      console.log(shop_records_mnt);
    }

    axios
      .get(
        "https://spreadsheets.google.com/feeds/list/1tdTxwv8j_De1VTbBhYMwC0B3B6_ZdIBgBVOdkxE0FJI/1/public/values?alt=json"
      )
      .then((response) => parse_data(response.data.feed.entry));
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
</style>
