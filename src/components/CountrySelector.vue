<template>
  <select
    @change="onChange"
    v-model="selected"
    class="form-select block border pd-3 rounded mt-10"
  >
    <option value="0">Select country...</option>
    <option
      v-for="country in countries"
      :key="country.CountryCode"
      :value="country.ID"
    >
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CountrySelector",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => item.ID === this.selected);
      console.log(country);
      this.$emit("get-country", country);
    },
  },
};
</script>
