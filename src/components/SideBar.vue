<template>
  <aside
    class="sidebar w-48 md:shadow transform -translate-x-full md:translate-x-0 transition-transform duration-150 ease-in bg-white"
  >
    <div class="sidebar-header flex items-center justify-center py-4">
      <div class="inline-flex">
        <Header />
      </div>
    </div>
    <div class="sidebar-content px-4 mt-0">
      <ul class="flex flex-col w-full">
        <li class="my-px">
          <a
            href="#"
            class="flex flex-row items-center h-10 px-3 mb-3 rounded-lg sm:text-xs text-purple-900 bg-blue-50 font-bold"
          >
            <span class="flex items-center justify-center text-purple-900">
              <i class="fa fa-globe"></i>
            </span>
            <span class="ml-3">Overview</span>
          </a>
        </li>
        <li class="my-px">
          <a
            href="#"
            class="flex flex-row items-center h-10 px-3 rounded-lg sm:text-xs text-gray-400"
          >
            <span class="flex items-center justify-center">
              <i class="fa fa-map"></i>
            </span>
            <span class="ml-3">World Map</span>
          </a>
        </li>
      </ul>
    </div>
  </aside>
</template>

<script>
import Header from "./Header";
export default {
  name: "SideBar",
  components: {
    Header,
  },
};
</script>
