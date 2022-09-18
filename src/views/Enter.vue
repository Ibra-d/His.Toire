<template>
  <div class="enter">
    <!-- <video src="../assets/v1.mp4" autoplay muted loop class="video-bg"></video> -->
    <div class="cursor" id="cursor"></div>
    <div class="black-T"></div>
    <div class="transition">
      <p>his.toire</p>
    </div>
    <div class="transition-1"><p>his.toire</p></div>
    <button class="button" @click="setPersistance(4000)">
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

    const setPersistance = (time) => {
      gsap.to(".button ", {
        translateY: "20em",
        ease: Expo.easeIn,
        duration: 1,
        opacity: 0,
      });

      gsap.to(".black-T", {
        delay: 1,
        left: 0,
        ease: Expo.easeInOut,
        duration: 2,
      });

      gsap.to(".black-T", {
        delay: 2,
        ease: Expo.easeInOut,
        duration: 1,
        backgroundColor: "#998c6a",
      });

      setTimeout(function () {
        router.push("/");
      }, time);
    };

    $(document).ready(function () {
      gsap.to(".black-T", {
        duration: 3,
        left: "100%",
        ease: Expo.easeInOut,
      });

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

      $(document).on("mousemove", function (e) {
        $(".cursor").css({
          width: "10px",
          height: "10px",
          position: "absolute",
          top: e.clientY,
          left: e.clientX,
          translate: "-50% -50%",
          transition: "100ms",
          // "border-radius": "50%",
          rotate: "45deg",
          "background-color": "#fff",
        });
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
  background-position: center;
  background-size: cover;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  // background-color: rgb(60, 59, 59);
  background: url("https://wallpaper.dog/large/10881766.jpg");

  .video-bg {
    z-index: -10;
    position: fixed;
    top: 0;
    left: 0;
  }

  .transition,
  .transition-1 {
    display: flex;
    justify-content: center;
    align-items: center;

    p {
      padding: 1em 2em;
      border: 2px solid #fff;
      font-size: 2em;
    }
  }

  .black-T {
    position: fixed;
    height: 100vh;
    width: 150%;
    top: 0;
    left: -50%;
    background-color: #3c3c3c;
    z-index: 10;
    overflow: hidden;
  }

  .transition {
    position: fixed;
    height: 50vh;
    width: 0%;
    top: 0;
    left: -100%;
    z-index: 10;
    overflow: hidden;
    background-color: #484848;
  }

  .transition-1 {
    position: fixed;
    height: 50vh;
    width: 0%;
    bottom: 0;
    left: -100%;
    z-index: 10;
    overflow: hidden;
    background-color: rgb(38 38 38);
  }

  .button {
    // backdrop-filter: blur(4px);
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
      mix-blend-mode: difference;
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
