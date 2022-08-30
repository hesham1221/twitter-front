<template>
 <div class="container">
  <div class="left">
    <img class="tIcon" src="../assets/twitter-icon-blue.svg" alt="twitter-icon" />
  </div>
  <div class="right">
<Left/>
  </div>
 </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Left from '../components/Left.vue'
@Options({
  components: {
    Left
  },
})
export default class HomeView extends Vue {}
</script>

<style scoped lang="scss">
.container{
  display: flex;
  width: 100vw;
  height: 100vh;
  .left{
    background-image: url('../assets/background.webp');
    flex: 0.57;
    display: flex;
    justify-content: center;
    align-items: center;
    .tIcon{
      padding-top: 40px;
      width: 30%;
    }
  }
  .right{
    background-color: black;
    flex : 0.43
  }
}
</style>
