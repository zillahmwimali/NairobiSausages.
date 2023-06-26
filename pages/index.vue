<template>
  <div>
    <main>
      <section class="absolute w-full h-full">
        
        <div class="container mx-auto  h-full">
          <div class="flex content-center items-center justify-center h-full">
            <div class="w-full lg:w-4/12 px-2 ">
       <div class="relative flex flex-col min-w-0 break-words w-full mb-6 lg:shadow-lg rounded-lg bg-[#fff] border-0">


                <div class="rounded-t mb-10 px-6 py-20">
                    <div class="absolute top-0 left-0 w-full h-1/3">
                    <img src="~/static/LoginBg.png" class="object-cover object-center rounded-t-md w-full h-full" alt="Background Image" />
                    </div>                 
                  
                </div>
                  <div class="flex justify-center mb-4 ">
                      <img src="../static/NsLogo.png" alt="Logo" class="mx-auto " />
                    </div>
                <div class="flex-auto px-4 lg:px-10 py-10 pt-0">
                  <form>
                    <div class="relative w-full mb-3">
                      <label
                        class="block  text-[#1C1B1F] text-xs font-bold mb-2"
                        for="grid-password"
                        >Enter your email address</label
                      ><input
                        type="email"
                        class="border-0 px-3 py-3 placeholder-[#9D9D9D] text-gray-700 bg-[#EEEEEE] rounded text-sm shadow focus:outline-none focus:ring w-full"
                        placeholder="Email"
                        style="transition: all 0.15s ease 0s;"
                        v-model="email"

                      />
                    </div>
                    <div class="relative w-full mb-3">
                      <label
                        class="block  text-[#1C1B1F] text-xs font-bold mb-2"
                        for="grid-password"
                        >Enter your password</label
                      ><input
                        type="password"
                        class="border-0 px-3 py-3 placeholder-[#9D9D9D] text-gray-700 bg-[#EEEEEE] rounded text-sm shadow focus:outline-none focus:ring w-full"
                        placeholder="Password"
                        style="transition: all 0.15s ease 0s;"
                        v-model="password"

                      />
                    </div>
                   
                    <div class="text-center mt-6">
                      <button
                        class="bg-[#212427] text-white active:bg-[#212427] text-sm font-bold px-6 py-3 rounded-full shadow hover:shadow-lg outline-none focus:outline-none mr-1 mb-1 w-full"
                        type="button"
                        style="transition: all 0.15s ease 0s;"
                        @click="login"

                      >
                        Login
                      </button>
                    </div>
                   <div class="text-gray-500 text-center mb-3 font-bold">
                        <small class="" style="letter-spacing: 0.1em;">Don't have an account?</small>
                        <small class="underline letter-spacing: 0.1em text-[#517148]">Register</small>
                    </div>

                   <div class="text-gray-500 text-center mb-3 font-bold">
                    <small class="underline letter-spacing: 0.1em text-[#517148]">Forgot password?</small>

                  </div>
                  </form>
                </div>
              </div>

              <div class="flex flex-wrap mt-6">
               
                
              </div>
            </div>
                <Modal
                    v-if="isFailed"
                    title="Login Failed"
                    message="Please check your credentials and try again."
                    :isOpen="true"
                    :isFailed="isFailed"
                    @close="isFailed = false"
                />

          </div>
        </div>
      </section>
    </main>
  </div>
</template>
<script>

import Modal from '@/components/Modal.vue';

export default {
  name: "login-page",
  data() {
    return {
      email: "",
      password: "",
      showModal: false,
      modalTitle: "",
      modalMessage: "",
      isFailed: false, 

    };
  },
  methods: {
    login() {
    
      if (this.email === "farmer@gmail.com" && this.password === "!farmer1234") {
        this.$router.push("/dashboard");
      } else {
        this.isFailed = true;
        this.showModal = true;
        this.modalTitle = "Login Failed";
        this.modalMessage = "Invalid credentials. Please try again.";
      
      }
    },
    closeModal() {
      this.showModal = false;
    }
  },
  components: {
    Modal
  }
};
</script>

