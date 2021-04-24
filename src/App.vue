<template>
  <div class="flex flex-row min-h-screen bg-gray-50 text-gray-800">
    <SideBar />

    <main
      class="main flex flex-col flex-grow -ml-48 md:ml-0 transition-all duration-150 ease-in"
    >
      <SearchBar />
      <router-view />
    </main>
  </div>
</template>

<script>
import SideBar from "@/components/SideBar";
import SearchBar from "@/components/SearchBar";

export default {
  components: {
    SideBar,
    SearchBar,
  },
};
</script>
