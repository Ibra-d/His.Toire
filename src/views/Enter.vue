<template>
  <div class="enter">
    <div class="transition">
      <video loop autoplay src="../assets/v1.mp4"></video>
    </div>
    <div class="transition-1">
      <video loop autoplay src="../assets/v2.mp4"></video>
    </div>
    <button class="button" @click="setPersistance">
      <strike>ENTER</strike>
      <p>ENTER</p>
    </button>
  </div>
</template>

<script>
import { gsap } from "gsap";
import { useRouter } from "vue-router";
export default {
  setup() {
    const router = useRouter();

    const setPersistance = () => {
      localStorage.setItem("persistance", "persistance");
      router.push("/");
    };

    $(document).ready(function () {
      gsap.to(".transition", {
        duration: 2,
        width: "100%",
        left: 0,
        ease: Expo.easeInOut,
      });
      gsap.to(".transition", {
        delay: 2,
        duration: 2,
        width: "100%",
        left: "100%",
        ease: Expo.easeInOut,
      });

      gsap.to(".transition-1", {
        delay: 0.1,
        duration: 2,
        width: "100%",
        left: 0,
        ease: Expo.easeInOut,
      });
      gsap.to(".transition-1", {
        delay: 2.3,
        duration: 2,
        width: "100%",
        left: "100%",
        ease: Expo.easeInOut,
      });
    });

    return {
      setPersistance,
    };
  },
};
</script>

<style lang="scss" scoped>
@import url(https://fonts.googleapis.com/css?family=Orbitron:regular,500,600,700,800,900);
.enter {
  height: 100vh;
  background-color: #000;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;

  .transition {
    position: fixed;
    height: 50vh;
    width: 0%;
    top: 0;
    left: -100%;
    z-index: 10;
    overflow: hidden;
  }

  .transition-1 {
    position: fixed;
    height: 50vh;
    width: 0%;
    bottom: 0;
    left: -100%;
    z-index: 10;
    overflow: hidden;
  }

  .button {
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: "Orbitron";
    border: 2px solid #fff;
    color: #fff;
    background: none;
    letter-spacing: 3px;
    font-size: 2em;
    padding: 0.5em 2em;
    cursor: pointer;
    transition: all 500ms;
    position: relative;
    overflow: hidden;
    animation: appear 6s cubic-bezier(0.86, 0, 0.07, 1);

    @keyframes appear {
      0% {
        opacity: 0;
        translate: 0 10em;
      }
    }

    p {
      translate: 1000%;
      position: absolute;
      transition: all 1s;
    }
    strike {
      transition: all 1s;
      transition-delay: 0.3s;
      animation: appear-1 4s 3s cubic-bezier(1, 0, 0, 1);

      @keyframes appear-1 {
        0% {
          opacity: 0;
          translate: -10em;
        }
      }
    }

    &:hover {
      color: #000;
      background-color: #fff;
      box-shadow: #ffffff78 0px 8px 24px;

      p {
        translate: 0;
      }
      strike {
        translate: -200%;
      }
    }
  }
}
</style>
