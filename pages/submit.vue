<template>

  <div class="sm:mx-40 ">

        <Header/>
  <div class="container mx-auto px-4 py-6 max-w-lg ">
    <form @submit.prevent="submitBatch">
    
      <div class="mb-4 ">
        <div class="relative">
          <div class="flex justify-between font-bold text-[#517148] py-4">
        <label class="block font-bold text-[#595959] " for="batch">Submit a Batch</label>
            <label class="absolute right-0 " for="batch">{{ batch }}</label>
          </div>
          <input
            v-model="batch"
            :min="min"
            :max="max"
            type="range"
            required
            class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer range-input"
          />
          <div class="flex justify-between text-sm font-bold text-[#000] py-2">
            <label class="absolute left-0 bottom-0" for="batch">{{ min }}</label>
            <label class="absolute right-0 bottom-0" for="batch">{{ max }}</label>
          </div>
        </div>
      </div>
      <div class="mb-4">
        <label class="block font-bold mb-2" for="breed">Breed</label>
        <select
          v-model="breed"
          id="breed"
          name="breed"
          class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none"
          required
          @change="updatePrice" 
        >
          <option value="" disabled selected>Large White</option>
          <option value="Large White">Large White</option>
          <option value="Duroc">Duroc</option>
          <option value="Hampshire">Hampshire</option>
          <option value="Landrace">Landrace</option>
          <option value="Berkshire">Berkshire</option>
        </select>
      </div>
      <div class="mb-4">
        <label class="block font-bold mb-2" for="age">Age</label>
        <select
          v-model="age"
          id="age"
          name="age"
          class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none"
          required
          @change="updatePrice"
        >
          <option value="" disabled selected>Select Age</option>
          <option value="6">6 months</option>
          <option value="12">12 months</option>
          <option value="18">18 months</option>
          <option value="24">24 months</option>
        </select>
      </div>
      <div class="mb-4">
        <label class="block font-bold mb-2" for="weight">Average Weight</label>
        <select
          v-model="weight"
          id="weight"
          name="weight"
          class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none"
          required
          @change="updatePrice"
        >
          <option value="" disabled selected>Select Weight</option>
          <option value="100">100 Kgs</option>
          <option value="150">150 Kgs</option>
          <option value="200">200 Kgs</option>
          <option value="250">250 Kgs</option>
        </select>
      </div>
      <div class="mb-4">
  <label class="block font-bold mb-2" for="pricePerPig">Ask Price per Pig</label>
  <input
    type="text"
    id="pricePerPig"
    name="pricePerPig"
    class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none"
    :value="pricePerPig"
    readonly
  />
</div>
<div class="mb-4">
  <label class="block font-bold mb-2" for="totalPrice">Total Price per Batch</label>
  <input
    type="text"
    id="totalPrice"
    name="totalPrice"
    class="w-full px-3 py-2 border border-gray-300 rounded focus:outline-none"
    :value="totalPrice"
    readonly
  />
</div>


      <button
        type="submit"
        class="bg-[#212427] w-full hover:bg-[#OOO] text-white font-bold py-4 px-4 rounded-full focus:outline-none"
        :disabled="!isFormValid"

      >
        Submit Request
      </button>
    </form>
     <Modal
        v-if="modalTitle && modalMessage"
        :title="modalTitle"
        :message="modalMessage"
        :isFailed="modalTitle === 'Submission Failed'"
        @close="modalTitle = ''"
/>
</div>

  </div>
</template>

<script>
import Modal from '@/components/Modal.vue';

export default {
  data() {
    return {
      batch: 0,
      min: 1,
      max: 50,
      breed: '',
      age: '',
      weight: '',
      showModal: false,
      modalTitle: "",
      modalMessage: "",
      isFailed: false, 
      pricePerPig: '',
      totalPrice: '',
      
    };
  },
  computed: {
    isFormValid() {
      return (
        this.batch &&
        this.breed &&
        this.age &&
        this.weight &&
        this.pricePerPig &&
        this.totalPrice
      );
    },
  },
  methods: {
    submitBatch() {
  if (!this.isFormValid) {
    this.modalTitle = 'Submission Failed';
    this.modalMessage = 'Please fill in all the fields.';
    return;
  }

  this.modalTitle = 'Submission Successful';
  this.modalMessage = 'Your Batch has successfully been submitted.';
},
    closeModal() {
      this.showModal = false;
    },

    updatePrice() {
      const age = parseFloat(this.age);
  const weight = parseFloat(this.weight);
  const batch = parseFloat(this.batch);

  if (age && weight && batch) {
    let calculatedPricePerPig = 0.0;
    let calculatedTotalPrice = 0.0;


    if (age <= 12 && weight <= 100) {
      calculatedPricePerPig = 1000;
    } else if (age <= 12 && weight <= 80) {
      calculatedPricePerPig = 1500;
    } else if (age <= 24 && weight <= 100) {
      calculatedPricePerPig = 2000;
    } else if (age <= 24 && weight <= 120) {
      calculatedPricePerPig = 2500;
    } else if (age <= 36 && weight <= 150) {
      calculatedPricePerPig = 3000;
    } else if (age <= 36 && weight <= 200) {
      calculatedPricePerPig = 3500;
    } else {
      calculatedPricePerPig = 4000;
    }
    
    calculatedTotalPrice = (calculatedPricePerPig * batch).toFixed(2);

this.pricePerPig = calculatedPricePerPig.toFixed(2);
this.totalPrice = calculatedTotalPrice;

  }
},


  },
  watch: {
  batch: 'updatePrice' 
},

};
</script>

<style>
.range-input {
  -webkit-appearance: none;
  appearance: none;
  border-radius: 5px;
  background: #D9D9D9;
  outline: none;
  opacity: 0.7;
  transition: opacity 0.2s;
}

.range-input:hover {
  opacity: 1;
}

.range-input::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #517148;
  cursor: pointer;
}

.range-input::-moz-range-thumb {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #007bff;
  cursor: pointer;
}
</style>
