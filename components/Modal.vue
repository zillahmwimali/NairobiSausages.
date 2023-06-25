<template>
  <div>
    <div class="fixed inset-0 flex items-center justify-center z-50">
      <div class="fixed inset-0 bg-gray-900 opacity-50 transition-opacity"></div>
      <div class="bg-white rounded-lg shadow-lg p-8 relative transform scale-100 transition ease-in">
        <div class="flex flex-col items-center">
          <template v-if="isFailed">
            <div class="flex items-center justify-center rounded-full bg-red-200 w-10 h-10 mb-2">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6 text-red-500"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M6 18L18 6M6 6l12 12"
                />
              </svg>
            </div>
          </template>
          <h2
            class="text-xl font-bold text-center"
            :class="{ 'text-red-500': isFailed }"
          >
            {{ title }}
          </h2>
        </div>
        <hr class="my-2">
        <div class="mb-4">
          <p>{{ message }}</p>
        </div>
        <div class="flex justify-center">
          <button
            @click="closeModal"
            class="px-4 py-2 bg-gray-300 rounded-md text-gray-700 mr-2"
          >
            Close
          </button>
         
        </div>
      </div>
    </div>
  </div>
</template>



<script>
export default {
  name: 'Modal',
  props: {
    title: {
      type: String,
      required: true
    },
    message: {
      type: String,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: true
    },
    isFailed: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    closeModal() {
      this.$emit('close');
    },
  }
};
</script>
