<template >
    <div class=" flex flex-row  justify-center">
      <div class="w-1/3 mt-20">
        <h1 class="font-sans text-left ml-10 mb-5 font-bold text-5xl text-black">
          Welcome Back <span class="text-blue-500">!</span>
        </h1>
        <h1 class="text-base font-sans text-left ml-10 mb-5  font-bold  text-grey">
          Don't have an account yet? <router-link to="/register"> <span class="text-base text-blue-700 hover:text-purple-700">Sign Up</span></router-link>
        </h1>
        <form class="rounded px-8 pt-6 pb-8 mb-4">
          <div class="mb-4">
          
            <input
              class="
                shadow
                bg-gray-500
                appearance-none
                border-2 border-gray-500
                rounded-xl
                w-full
                py-4
                px-4
                text-white
                leading-tight
                focus:outline-none focus:bg-gray focus:border-purple-500
              "
              type="text"
              name="email"
              placeholder="email"
              v-model="email"
            />
          </div>
          <div class="mb-6">
            
            <input
              class="
                 shadow
                bg-gray-500
                appearance-none
                border-2 border-gray-500
                rounded-xl
                w-full
                py-4
                px-4
                text-white
                leading-tight
                focus:outline-none focus:bg-gray focus:border-purple-500
              "
              type="password"
              name="password"
              placeholder="password"
              v-model="password"
            />
          
            <p class="mt-4 text-red-500 text-xs italic">
              {{ ExistError }}
            </p>
            <p class="mt-4 text-red-500 text-xs italic">
              {{ error }}
            </p>
          </div>
          <div class="flex items-center justify-between">
            <button
              @click="signin"
              class="
                bg-blue-700
                hover:bg-purple-700
                text-white
                font-medium
                text-sm
                py-3
                px-4
                rounded-xl
                focus:outline-none focus:shadow-outline
                w-40
              "
              type="button"
            >
              Sign In
            </button>
            <a
              class="
                inline-block
                align-baseline
                font-bold
                text-sm text-blue-700
                hover:text-blue-800
                
              "
              href="#"
            >
              Forgot Password?
            </a>
          </div>
        </form>
        
      </div>
      <div class="w-1/3 mt-20">&nbsp;</div>
      
    </div>  
    <p class="mt-20 text-center text-gray-500 text-xs">
          &copy;2020 All rights reserved.
        </p>
</template>

<script>
import AuthService from "../services/AuthService.js";
// import Axios from 'axios'

export default {
  data() {
    return {
      email: "",
      password: "",
      error: null,
      ExistError: null,
    };
  },
  methods: {
    async signin() {
      AuthService.login({
        email: this.email,
        password: this.password,
      })
        .then((response) => {
          console.log("This is the response", response);
          this.$router.push("/");
          this.error = response.response.data.message;
        })
        .catch((error) => {
          console.log("This is the response", error);
          this.ExistError = error.response.data.status;
          this.error = error.response.data.message;
        });
    }
  },
  components: {},
};
</script>
