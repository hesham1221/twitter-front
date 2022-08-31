<template>
  <div class="grey">
    <div class="modal">
      <form @submit="submit" class="content">
        <h1>{{ title }}</h1>
        <h3>Username :</h3>
        <input
          @change="username = $event.target.value"
          type="text"
          placeholder="Username..."
          :disabled="loading"
          :class="[error ? 'err' : '']"
        />
        <!-- <h3 v-if="title === 'Sign Up'">Email :</h3>
        <input
          v-if="title === 'Sign Up'"
          @change="email = $event.target.value"
          type="email"
          placeholder="Email..."
          :disabled="loading"
        /> -->
        <h3>Password :</h3>
        <input
          @change="password = $event.target.value"
          type="password"
          placeholder="Password..."
          :disabled="loading"
          :class="[error ? 'err' : '']"
        />
        <Button content="Submit" />
        <Button @onClick="cancel" content="Cancel" />
        <div v-if="loading" class="lds-ring">
          <div></div>
          <div></div>
          <div></div>
          <div></div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Button from "./Button.vue";
import axios from "axios";
export default {
  name: "Modal",
  props: {
    title: String,
  },
  components: { Button },
  data() {
    return {
      username: "",
      password: "",
      email: "",
      loading: false,
      error: false,
    };
  },
  methods: {
    cancel() {
      this.$emit("greyClick");
    },
    async submit(e) {
      e.preventDefault();
      this.loading = true;
      console.log(this.title);
      try {
        if (this.title !== "Sign Up") {
          const res = await axios({
            method: "POST",
            url: "http://localhost:5000/graphql",
            data: {
              query: ` {
                           login(loginInput:{
                               username: "${this.username}"
                               password : "${this.password}"
                           }){
                               token
                               username
                           }
                           }
                        `,
            },
          });
          const data = res.data.data.login;
          const token = data.token;
          localStorage.setItem('baianat-twitter' ,token)
          this.$emit('isLogin')
        } else {
          const res = await axios({
            method: "POST",
            url: "http://localhost:5000/graphql",
            data: {
              query: ` mutation{
  createAuthor(createAuthorInput :{
    username :"${this.username}"
    password : "${this.password}"
  }){
    username
    id
  }
}
                        `,
            },
          });
          const data = res.data.data.createAuthor;
          
        }
      } catch (error) {
        this.loading = false;
        this.error = true;
        console.log("eror");
      }
      this.loading = false;
    },
  },
};
</script>
<style lang="scss">
.grey {
  position: absolute;
  width: 100vw;
  height: 100vh;
  color: rgba(128, 128, 128, 0.199);
  display: grid;
  place-content: center;

  .modal {
    height: 100%;
    width: 100%;
    display: grid;
    place-items: center;
    .lds-ring {
      display: inline-block;
      position: relative;
      width: 80px;
      height: 80px;
    }
    .lds-ring div {
      box-sizing: border-box;
      display: block;
      position: absolute;
      width: 64px;
      height: 64px;
      margin: 8px;
      border: 8px solid #1a8cd8;
      border-radius: 50%;
      animation: lds-ring 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
      border-color: #1a8cd8 transparent transparent transparent;
    }
    .lds-ring div:nth-child(1) {
      animation-delay: -0.45s;
    }
    .lds-ring div:nth-child(2) {
      animation-delay: -0.3s;
    }
    .lds-ring div:nth-child(3) {
      animation-delay: -0.15s;
    }
    @keyframes lds-ring {
      0% {
        transform: rotate(0deg);
      }
      100% {
        transform: rotate(360deg);
      }
    }

    .content {
      background-color: rgba(20, 20, 20, 0.795);
      display: flex;
      flex-direction: column;
      min-width: 500px;
      width: 30vw;
      height: 80vh;
      border-radius: 70px;
      justify-content: center;
      padding: 0 30px;
      align-items: center;
      h1 {
        font-size: 55px;
        margin-bottom: 30px;
      }

      h3 {
        margin-bottom: 15px;
      }

      input {
        width: 70%;
        min-width: 70px;
        padding: 13px;
        margin-bottom: 30px;
        color: black;
        font-size: 15px;
        border-radius: 13px;
        border: none;
        &:focus {
          outline: none;
        }
      }
      .err {
        border: 1.5px rgba(230, 4, 4, 0.842) solid;
        box-shadow: 0px 4px 14px 8px rgba(237, 104, 104, 0.23);
        -webkit-box-shadow: 0px 4px 14px 8px rgba(237, 104, 104, 0.23);
        -moz-box-shadow: 0px 4px 14px 8px rgba(237, 104, 104, 0.23);
      }
    }
  }
}
</style>
