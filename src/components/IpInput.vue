<template>
  <div class="ip-input flex flex-col items-center justify-between relative">
    <h1 class="text-white text-center pt-10 pb-10 text-2xl md:text-3xl">IP Address Tracker</h1>
    <form class="w-full flex items-center justify-center">
      <input
        name="IpAddressValue"
        class="p-3 pl-5 outline-none md:p-6 w-9/12 md:w-1/3"
        type="text"
        ref="ipAddress"
        v-model="form.ipAddress"
        placeholder="Search for any IP address or domain"
        style="font-size: 20px;"
      >
      <button
        class="p-5 md:p-8 outline-none :hover:outline-none"
        @click="showLocation"
      ><svg xmlns="http://www.w3.org/2000/svg" width="11" height="14"><path fill="none" stroke="#FFF" stroke-width="3" d="M2 1l6 6-6 6"/></svg></button>
    </form>
    <ip-result
      :ip="ip"
      :city="city"
      :region="region"
      :postal="postal"
      :timezone="timezone"
      :isp="isp"
    />
    <ip-map
      :lat="lat"
      :lng="lng"
    />
  </div>
</template>

<script>
import IpResult from './IpResult.vue'
import IpMap from './IpMap.vue'

const axios = require('axios');

export default {
  components: {
    'ip-result' : IpResult,
    'ip-map' : IpMap
  },
  name: 'IpInput',
  data() {
    return {
      form: {
        ipAddress: ''
      },
      ip: '',
      city: '',
      region: '',
      postal: '',
      timezone: '',
      isp: '',
      lat: '',
      lng: ''
    }
  },
  mounted() {
    this.setValues();
  },
  methods: {
    showLocation(e) {
      e.preventDefault();
      const key = "at_9pbNimn2UsiRbkNgzK39yuKDjOhvr";
      const address = this.form.ipAddress;
      axios
        .get(`https://geo.ipify.org/api/v1?apiKey=${key}&ipAddress=${address}`)
        .then( (response) => this.getLocation(response.data))
        .catch(function (error) {
          console.log(error);
        });
    },
    setValues() {
      this.ip =  '192.212.174.101';
      this.city = 'Brooklyn';
      this.region = 'NY';
      this.postal = '10001';
      this.timezone = '-05:00';
      this.isp = 'SpaceX Starlink';
      this.lat = '47.413220';
      this.lng = '-1.219482';
    },
    getLocation(data) {
      this.ip = data.ip;
      this.city = data.location.city;
      this.region = data.location.region;
      this.postal = data.location.postalCode;
      this.timezone = data.location.timezone;
      this.isp = data.isp;
      this.lat = data.location.lat;
      this.lng = data.location.lng;
    }
  }
  
  // props: {
  //   msg: String
  // }
}
</script>

<style scoped>
.ip-input {
  background: url("../assets/images/pattern-bg.png");
  height: 22rem
}
.ip-input input {
  border-bottom-left-radius: 1.2em;
  border-top-left-radius: 1.2em;
}
button {
  background-color: #000000;
  border-bottom-right-radius: 1.2em;
  border-top-right-radius: 1.2em;
}
button:hover {
  cursor: pointer;
  background-color: #3F3F3F;
}
form {
  padding-bottom: 9.4rem
}
@media screen and (max-width: 768px) {
  .ip-input input {
    border-bottom-left-radius: 0.6em;
    border-top-left-radius: 0.6em;
  }
  button {
    background-color: #000000;
    border-bottom-right-radius: 0.6em;
    border-top-right-radius: 0.6em;
  }
}
</style>
