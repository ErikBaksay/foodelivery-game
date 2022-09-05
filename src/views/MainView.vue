<template>
  <div class="container">
    <GameContainer></GameContainer>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import GameContainer from "@/components/GameContainer.vue";

@Options({
  components: {
    GameContainer,
  },
})
export default class MainView extends Vue {}
</script>

<style lang="sass">
.container
  height: 100vh
  width: 100vw
  display: flex
  justify-content: center
  align-items: center
</style>
