<template>
  <div class="home">
    <img class="logo" alt="Vue logo" src="../assets/logo.webp" />
    <HelloWorld msg="La Karamerie arrive bientôt" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'
import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

@Options({
  components: {
    HelloWorld
  }
})
export default class HomeView extends Vue {}
</script>

<style scoped>
.logo {
  width: 20%;
}

@media (max-width: 760px) {
  .logo {
    margin-top: 100px;
    width: 50%;
  }
}
</style>
