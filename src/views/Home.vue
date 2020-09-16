<template>
  <div class="home">
    <input type="text" v-model="postNum">
    <button @click="showAddress">住所自動入力</button>
    <p>Address:{{fullAddress}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      postNum: "",
      fullAddress: ""
    };
  },
  methods: {
    async showAddress() {
      let address = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.postNum}?fields=allAddress&apiKey=kGhJYIXeG9NicR9te8n9NHjd1tIB6Q5JOYf3uAh`);
      this.data = address.data[0];
      this.fullAddress = this.data.allAddress;
      // console.log(address);
    }
  }
};
</script>
