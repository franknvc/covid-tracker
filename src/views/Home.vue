<template>
  <div v-if="!loading" class="flex-1 overflow-x-hidden overflow-y-auto">
    <div class="container px-5 py-2">
      <DataTitle :text="title" :dataDate="dataDate" />
      <DataBox :stats="stats" />
      <CountrySelector @get-country="getCountryData" :countries="countries" />
      <button
        @click="clearCountryData"
        v-if="stats.Country"
        class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600"
      >
        Clear
      </button>
    </div>
  </div>

  <div v-else class="flex-1 overflow-x-hidden overflow-y-auto bg-gray-200">
    <div class="container mx-auto px-6 py-8">
      <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching data</div>
      <div class="w-30 m-auto">
        <hollow-dots-spinner
          :animation-duration="1000"
          :dot-size="24"
          :dots-num="3"
          color="#ff1d5e"
          margin="auto"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { HollowDotsSpinner } from "epic-spinners";
import DataTitle from "@/components/DataTitle";
import DataBox from "@/components/DataBox";
import CountrySelector from "@/components/CountrySelector";

export default {
  name: "Home",
  components: {
    HollowDotsSpinner,
    DataTitle,
    DataBox,
    CountrySelector,
  },
  data() {
    return {
      loading: true,
      title: "World Overview",
      dataDate: "",
      stats: {},
      countries: [],
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },

    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },

    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = "Global";
      this.stats = data.Global;
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
