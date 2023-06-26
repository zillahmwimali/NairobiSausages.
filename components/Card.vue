<template>
  <div class="w-1/2 sm:w-1/2 md:w-1/3 lg:w-1/4 px-4 mb-4">
    <div class="bg-white rounded-md shadow-lg p-6">
      <div class="text-left text-green-800 text-xs">{{ cName }}</div>
      <div class="flex items-center mb-4">
        <div class="text-2xl font-bold">{{ number }}</div>
        <div class="w-px h-6 bg-gray-300 mx-4"></div>
        <div class="text-sm font-semibold">
          <div class="md:flex md:flex-wrap">
            {{ text }}
          </div>
        </div>
      </div>

      <button class="px-4 py-2 rounded-full whitespace-nowrap font-bold" :style="{ backgroundColor: buttonColor, color: buttonTextColor }"  @click="redirectToEndpoint">{{ buttonLabel }}</button>
    </div>
  </div>
</template>



<script>
export default {
  name: 'Card',
  props: {
    number: {
      type: Number,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
    buttonColor: {
      type: String,
      default: 'blue',
    },
    buttonLabel: {
    type: String,
    default: 'blue',
    },
     buttonTextColor: {
      type: String,
      default: 'white',
    },
    cName:{
        type:String,
        required:true,
    },
    endpoint:{
        type:String,
        required:true,
    },
  },
  computed: {
    buttonClasses() {
      return [
        'bg-' + this.buttonColor + '-500',
        'text-white',
        'py-2',
        'px-4',
        'rounded-full',
        'hover:bg-' + this.buttonColor + '-600',
      ];
    },
  },
   methods: {
    redirectToEndpoint() {
      this.$router.push(this.endpoint);
    }
},
};
</script>

<style scoped>
/* Add custom styles for the Card component here */
</style>
