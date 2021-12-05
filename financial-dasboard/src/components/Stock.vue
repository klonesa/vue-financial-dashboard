<template>
  <div>
    <nav class="navbar navbar-dark bg-dark " style="height: 80px">
      <h1 class="text-white m-2">Financial Dashboard</h1>
      <div class="btn-group m-3" role="group" aria-label="Basic example">
        <button type="button" class="btn btn-outline-secondary text-white">Admin</button>
        <button type="button" class="btn btn-outline-secondary text-white">Guest</button>
      </div>
    </nav>
    <div class="hello">
      <div class="container">
        <form class="navbar-form m-2">
          <div class="input-group no border">
            <input
              type="text"
              value=""
              class="form-comntrol"
              placeholder="Search..."
              v-model="stock"
            />
            <button
              @click="update(stock)"
              class="btn btn-white btn-round bn-just-icon"
            >
              <i class="material-icons ml-3">search</i>
            </button>
          </div>
        </form>
        <!-- <div class="row">
        <div class="col-md-3">
          <div class="btn-group" role="group" aria-label="Basic example">
            <button type="button" class="btn btn-outline-secondary">Daily</button>
            <button type="button" class="btn btn-outline-secondary">Weekly</button>
            <button type="button" class="btn btn-outline-secondary">Montly</button>
          </div>
        </div>
      </div> -->
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Stock",
  props: {
    msg: String,
  },
  data() {
    return {
      stock: "",
      infoCompany: "",
    };
  },
  methods: {
    update(stock) {
      // console.log(stock);
      this.getInfo(stock);
    },
    getInfo(stock) {
      console.log(stock);
      axios
        .get(
          // "https://financialmodelingprep.com/api/v4/company-outlook?symbol=AAPL&apikey=e77bafdd8b20ee59904e279c50368683"
          // "https://financialmodelingprep.com/api/v3/profile/AAPL?apikey=e77bafdd8b20ee59904e279c50368683"
          `https://financialmodelingprep.com/api/v3/profile/${stock}?apikey=e77bafdd8b20ee59904e279c50368683`
        )
        .then((res) => {
          this.infoCompany = res.data;//.profile
        })
        .catch((err) => console.log(err));
         console.log(this.infoCompany);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
