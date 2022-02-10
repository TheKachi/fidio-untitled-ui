<template>
  <div class="">
    <div
      class="flex flex-col md:flex-row md:justify-between md:items-center gap-y-16 mb-32"
    >
      <div>
        <h1 class="text-lg md:text-xl text-gray-900 font-medium">
          Welcome back, {{ user.name }}
        </h1>
        <p class="text-base text-gray-500">
          Track, manage and forecast your customers and orders.
        </p>
      </div>

      <!-- todo: make buttons components  -->
      <div class="flex gap-12">
        <button class="border-gray text-gray-700">
          <span><svg-loader icon="import" path="img/svgs" /></span>
          Import
        </button>
        <button class="bg-primary text-white">
          <svg-loader icon="plus" path="img/svgs" />
          Add
        </button>
      </div>
    </div>
    <!-- Stats  -->
    <div class="grid grid-cols-12 gap-20 md:gap-24">
      <div
        class="col-span-12 md:col-span-4 p-20 md:px-24"
        v-for="(stat, i) in stats"
        :key="i"
      >
        <!-- todo: consider converting into a component with props -->
        <div class="border-gray shadow rounded-lg">
          <div class="mb-20 md:mb-24 flex justify-between items-center">
            <h3 class="text-base text-gray-900 font-medium">
              {{ stat.name }}
            </h3>
            <button class="p-0 border-0">
              <i class="fas fa-ellipsis-v text-gray-300 h-8"></i>
            </button>
          </div>
          <h4 class="text-xl md:text-2xl text-gray-900 font-semibold">
            {{ stat.numbers }}
          </h4>
          <div>
            <h5>{{ stat.percent }}%</h5>
            <span>vs last month</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import svgLoader from "~/components//svg-loader.vue";

export default {
  name: "IndexPage",

  layout: "layout",

  data() {
    return {
      user: {
        name: "Olivia",
      },

      stats: [
        {
          name: "Total customers",
          numbers: "2420",
          percent: 40,
          isUp: true,
        },

        {
          name: "Members",
          numbers: "1210",
          percent: 10,
          isUp: false,
        },
        {
          name: "Active now",
          numbers: "316",
          percent: 20,
          isUp: true,
        },
      ],
    };
  },

  components: {
    svgLoader,
  },
};
</script>
