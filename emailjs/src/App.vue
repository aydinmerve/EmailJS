<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
    <h2 class="d-flex justify-content-center mb-4 mt-2">
            Takip etmek için kayıt ol
          </h2>
     <form @submit.prevent="sendEmail" class="align-items-center mt-3 align-self-center">


            <b-modal
                    id="modal-center"
                    centered
                    title="Success"
                    title-class="font-18"
                    hide-footer
                    v-model="success"
                  ></b-modal>
          <div class="form-group pl-4">
            <label class="text-justify" for="exampleInputPassword1"
              >Name Surname</label
            >
            <input
            name="name"
              v-model="name"
              style="height: 40px"
              type="text"
              class="form-control"
              id="text"
              placeholder="Name Surname"
              required
            />
          </div>

          <div class="form-group mt-4">
            <label class="text-justify" for="exampleInputEmail1"
              >Email address</label
            >
            <input
             required
             name="email"
              style="height: 40px"
              type="email"
              class="form-control w-100"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
              placeholder="Enter your email"
              v-model="email"
            />
          </div>
          <br />
          <b-form-checkbox
            id="checkbox-1"
            v-model="status"
            name="checkbox-1"
            value="accepted"
            unchecked-value="not_accepted"
          >
          </b-form-checkbox>
          <button
          value="Send"
            type="submit"

            class="btn btn-primary mt-3 mb-4 w-100"
          >
            Send Email
          </button>
        </form>

   
  </div>


  
</template>

<script>
import emailjs from 'emailjs-com';
export default {
  methods: {
    sendEmail(e) {
      try {
        emailjs.sendForm('merveaydin.ieee@gmail.com', 'template_karsgle', e.target,
        'user_segTKcmcTX4eZ14n8I2Ig',{
          name: this.name,
          email: this.email,

        })

      this.success=true;

      } catch(error) {
          console.log({error})
      }
      // Reset form field
      this.name = ''
      this.email = ''
    },
  },
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style lang="scss" scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
.btn-primary {
  background-color: #4dc2ca;
  border-color: #4dc2ca;
  height: 40px;
}

</style>
