<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <p>{{ var1 }}</p>
</template>

<script>
export default {
  name: "App",
  props: [],
  data() {
    return {
      request_url:
        "https://spreadsheets.google.com/feeds/list/1tdTxwv8j_De1VTbBhYMwC0B3B6_ZdIBgBVOdkxE0FJI/1/public/values?alt=json",
        shop_item : [],
        shop_price : [], 
        department_cat : []
    };
  },
  components: {},
  methods: {
    parse_data (json_payload){

      entries.forEach(
        (value)=>{
          temp_record = {
            "shop_item": value.gsx$winkelitem.t,
            "shop_price": value.gsx$prys.t,
            "dep": value.gsx$departement.t


          }

        }
      );







    }
  },
  mounted() {
    var1 = axios
      .get(request_url)
      .then((response));
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
