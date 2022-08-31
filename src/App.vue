<template>
  <div v-if="!islogin" class="container">
    <div class="left">
      <img
        class="tIcon"
        src="./assets/twitter-icon-blue.svg"
        alt="twitter-icon"
      />
    </div>
    <div class="right">
      <Left  @show="showModal" />
    </div>
    <Modal @isLogin="makeLogin" @greyClick="closeModal" :title="title" v-if="isClicked" />
  </div>
  <div v-if="islogin" class="container valid ">
    <MainLeft />
    <MainCenter />
    <MainRight />
  </div>
</template>

<script>
import Left from "./components/Left.vue";
import Modal from "./components/Modal.vue";
import axios from "axios";
import MainLeft from "./components/MainLeft.vue";
import MainCenter from "./components/MainCenter.vue";
import MainRight from "./components/MainRight.vue";

const myToken = localStorage.getItem("baianat-twitter");

const defaultApp = {
  name: "App",
  components: {
    Left,
    Modal,
    MainLeft,
    MainCenter,
    MainRight
  },
  created() {
    this.validateUser();
  },
  data() {
    return {
      isClicked: false,
      title: null,
      token: localStorage.getItem("baianat-twitter"),
      islogin: false,
      user: {},
    };
  },
  methods: {
    showModal(title) {
      this.isClicked = !this.isClicked;
      this.title = title;
    },
    makeLogin(){
      this.islogin = true
    },
    closeModal() {
      this.isClicked = false;
    },
    async validateUser() {
      console.log(myToken);
      try {
        const res = await axios({
          method: "POST",
          url: "http://localhost:5000/graphql",
          headers: {
            Authorization: "Bearer " + myToken,
          },
          data: {
            query: ` {
  validAuthor{
    id
    username
    numFollowers
    numFollowing
  }
            }
                        `,
          },
        });
        if (res.status === 200) {
          const data = res.data.data.validAuthor;
          this.islogin = true;
          this.user = { ...data };
        }
      } catch (error) {
        localStorage.removeItem("baianat-twitter");
      }
    },
  },
};

export default defaultApp;
</script>

<style lang="scss">
  
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
  color: white;
}

.valid {
  background-color: #121b24;
}
.container {
  display: flex;
  width: 100vw;
  height: 100vh;
  .left {
    background-image: url("./assets/background.webp");
    flex: 0.57;
    display: flex;
    justify-content: center;
    align-items: center;
    .tIcon {
      padding-top: 40px;
      width: 30%;
    }
  }
  .right {
    background-color: black;
    flex: 0.43;
  }
}
</style>
