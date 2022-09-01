<template>
  <div class="right-main">
    <div class="input-cnt">
      <i class="mag fa fa-search" aria-hidden="true"></i>
      <input type="text" placeholder="Search Tweeter..." />
    </div>
    <div class="authors-cont">
      <Author v-for="author in authors" :author="author" />
    </div>
  </div>
</template>

<script>
import Author from "./Author.vue";
import axios from 'axios'
export default {
  components: {
    Author,
  },
  data(){
    return {
        authors :[]
    }
  },
  created(){
    this.getAllAuthors()
  },
  methods : {
    async getAllAuthors(){
        try {
            const res = await axios({
                url : 'http://192.168.50.22:5000/graphql',
                method:'POST',
                data:{
                    query : `
                    {
      authors{
        username
        numFollowing
        numFollowers
      }
    }
                    `
                }
            })
            const authors = res.data.data.authors
            this.authors =[...authors]
        
        } catch (error) {
            console.log(error)    
        }
    }
  }
};
</script>

<style lang="scss">
.right-main {
  display: flex;
  flex-direction: column;
  flex: 0.33;
  padding: 12px;
  .input-cnt {
    padding: 12px;
    border-radius: 20px;
    background-color: rgba(52, 50, 58, 0.829);
    display: flex;
    align-items: center;
    width: 100%;
    .mag {
      padding: 0 9px;
      margin-bottom: 1px;
      color: rgba(128, 128, 128, 0.644);
    }
    input {
      width: 100%;
      background-color: transparent;
      border: none;
      font-size: 14px;

      &:focus {
        outline: none;
      }
    }
  }
  .authors-cont{
    padding: 20px;
    overflow-y: scroll;
    &::-webkit-scrollbar{
        background-color: transparent;
    }
  }
}
</style>
