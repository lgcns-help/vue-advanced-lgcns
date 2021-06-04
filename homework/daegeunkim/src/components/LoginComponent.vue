<template>
  <div>
    <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
      @submit.prevent="signIn">
      <!-- name area-->
      <div class="mb-4">
        <label class="block text-grey-darker text-sm font-bold mb-2" for="username">
          Username
        </label>
        <input v-model="name"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker leading-tight focus:outline-none focus:shadow-outline"
          id="username" type="text" placeholder="Username">
      </div>
      <!-- password area-->
      <div class="mb-6">
        <label class="block text-grey-darker text-sm font-bold mb-2" for="password">
          Password
        </label>
        <input v-model="pwd"
          v-bind:class="{'border-red': isPwdOutOfFormat}"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker mb-3 leading-tight focus:outline-none focus:shadow-outline"
          id="password" type="password" placeholder="******************">
        <div v-if="isPwdOutOfFormat">
          <p class="text-red text-xs italic">Please choose a password.</p>
        </div>
      </div>
      <!-- button area -->
      <div class="flex items-center justify-between">
        <button class="bg-blue hover:bg-blue-dark text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="submit">
          Sign In
        </button>
        <a class="inline-block align-baseline font-bold text-sm text-blue hover:text-blue-darker" href="#">
          Forgot Password?
        </a>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'LoginComponent',
  data: function() {
    return {
      name: '',
      pwd: '',
      isPwdOutOfFormat: true
    }
  },
  watch: {
    pwd: function(val) {
      if(val.length > 0){
        this.isPwdOutOfFormat = false;
      }
      else{
        this.isPwdOutOfFormat = true;
      }
    }
  },
  methods: {
    signIn: function() {
      fetch('https://jsonplaceholder.typicode.com/users/', {
        method: 'POST',
        dataType: 'json',
        contentType: 'application/json; charset=UTF-8',
        data: JSON.stringify({
          name: this.name,
          password: this.pwd
        })
      })
      .then((res) => {
        console.log(res.body);
        this.name = '';
        this.pwd = '';
      })
      .catch((err) => {
        console.log(err);
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
