<template>
  <div class="grid md:grid-cols-3 gap-10 md:gap-5">
    <!-- Total cases -->
    <div
      class="shadow-md bg-gray-30 p-3 text-left rounded border-4 border-indigo-900"
    >
      <div class="flex flex-row items-baseline">
        <h3 class="text-lg md:text-xs xl:text-xl 2xl:text-2xl mb-4">
          Total Cases
        </h3>
        <div class="flex ml-auto">
          <i
            class="fa fa-lungs-virus text-3xl md:text-xl xl:text-4xl 2xl:text-5xl text-indigo-900"
          ></i>
        </div>
      </div>
      <div
        class="text-3xl md:text-lg xl:text-4xl 2xl:text-5xl font-bold text-blue-900"
      >
        {{ numberCommaDivider(stats.TotalConfirmed) }}
      </div>
    </div>

    <!-- Total deaths -->
    <div
      class="shadow-md bg-gray-30 p-3 text-left rounded border-4 border-red-900"
    >
      <div class="flex flex-row items-baseline">
        <h3 class="text-lg md:text-xs xl:text-xl 2xl:text-2xl mb-4">
          Total Deaths
        </h3>
        <div class="flex ml-auto">
          <i
            class="fa fa-skull-crossbones text-3xl md:text-xl xl:text-4xl 2xl:text-5xl text-red-900"
          ></i>
        </div>
      </div>
      <div
        class="text-3xl md:text-lg xl:text-4xl 2xl:text-5xl font-bold text-red-900"
      >
        {{ numberCommaDivider(stats.TotalDeaths) }}
      </div>
    </div>

    <!-- Total recovered -->
    <div
      class="shadow-md bg-gray-30 p-3 text-left rounded border-4 border-green-900"
    >
      <div class="flex flex-row items-baseline">
        <h3 class="text-lg md:text-xs xl:text-xl 2xl:text-2xl mb-4">
          Total Recovery
        </h3>
        <div class="flex ml-auto">
          <i
            class="fa fa-heartbeat text-3xl md:text-xl xl:text-4xl 2xl:text-5xl text-green-900"
          ></i>
        </div>
      </div>
      <div
        class="text-3xl md:text-lg xl:text-4xl 2xl:text-5xl font-bold text-green-900"
      >
        {{ numberCommaDivider(stats.TotalRecovered) }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataBox",
  props: ["stats"],
  methods: {
    numberCommaDivider(n) {
      return n.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>
