<template>
  <div id="path"></div>
  <div class="car drive1" id="car1"></div>
</template>

<script lang="ts">
import { transform } from "@vue/compiler-core";
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    msg: String,
  },
})
export default class GameContainer extends Vue {
  mounted() {
    let path = document.getElementById("path");
    const pathWidth = 60;
    let car1 = document.getElementById("car1");
    let pathRect = path!.getBoundingClientRect();
    let startingPoint = {
      x: pathRect.left + "px",
      y: (pathRect.top + pathWidth / 2 - 15).toString() + "px",
    };
    car1!.style.left = startingPoint.x;
    car1!.style.top = startingPoint.y;

    /* eslint-disable */
    if (car1!.classList.contains("drive1")) {
      car1!.animate(
        [
          {
            transform: "translate(0px, 0px) rotate(0deg)", 
            offset: 0,
          },
          {
            transform: "translate(" + (pathRect.width - pathWidth).toString() + "px, 0px) rotate(0deg)", 
            offset: 0.24,
          },
          {
            transform: "translate(" + (pathRect.width - pathWidth).toString() + "px, 0px) rotate(90deg)", 
            offset: 0.25,
          },
          {
            transform:
              "translate("+(pathRect.width - pathWidth).toString()+ "px, " + (pathRect.height - pathWidth).toString() + "px) rotate(90deg)",
            offset: 0.49,
          },
          {
            transform:
              "translate("+(pathRect.width - pathWidth).toString()+ "px, " + (pathRect.height - pathWidth).toString() + "px) rotate(180deg)",
            offset: 0.5,
          },
          {
            transform:
              "translate( 0px, "+ (pathRect.height - pathWidth).toString() + "px) rotate(180deg)",
            offset: 0.74,
          },
          {
            transform:
              "translate( 0px, "+ (pathRect.height - pathWidth).toString() + "px) rotate(270deg)",
            offset: 0.75,
          },
          {
            transform:
              "translate(0px, 0px) rotate(270deg)",
            offset: 0.99,
          },
          {
            transform:
              "translate(0px, 0px) rotate(360deg)",
            offset: 1,
          },
        ],
        {
          duration: 10000,
          iterations: Infinity,
        }
      );
    }
    /* eslint-enable */
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
#path
  height: 400px
  width: 400px
  border: 60px #cbcbcb solid
  border-radius: 25px
  position: relative
.car
  height: 30px
  width: 60px
  border-radius: 10px
  background: red
  position: absolute
.drive1
  animation: drive1Animation 10s linear infinite
</style>
