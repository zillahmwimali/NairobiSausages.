<template>
  <div class="w-full md:w-1/3 lg:w-1/4 px-4 mb-4">
    <div class="bg-white rounded-lg shadow-lg flex sm:flex-col">
      <img :src="image" alt="Post Image" class="w-1/4 sm:h-48  sm:w-full h-1/4 object-cover rounded-t-lg p-2 sm:p-0" />
      <div class="p-4 flex flex-col justify-between">
        <div>
          <h3 class="text-xl font-semibold mb-2">{{ title }}</h3>
          <p class="text-gray-600 text-sm mb-4">{{ description }}</p>
        </div>
        <div class="flex items-center justify-between capitalize">
            <span class="inline-block bg-blue-500 text-white text-xs px-2 py-1 rounded-full">{{ category }}</span>
            <span class="inline-block bg-gray-300 text-gray-700 text-xs px-2 py-1 rounded-full ml-4 sm:ml-auto">{{ category2 }}</span>
        </div>



      </div>
    </div>
  </div>
</template>





<script>
export default {
  name: 'PostCard',
  props: {
    image: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    category: {
      type: String,
      required: true,
    },
    category2: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
/* Add custom styles for the PostCard component here */
</style>
