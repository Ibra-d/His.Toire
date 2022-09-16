<template>
  <div class="home">
    <header>
      <div class="logo">
        <h1>HIS.TOIRE</h1>
      </div>
      <div class="contact">
        <h1>contact</h1>
      </div>
      <div class="border"></div>
    </header>
    <main>
      <div class="intro">
        <div class="text">
          <p>
            <span
              >Lorem ipsum, dolor sit amet consectetur adipisicing elit.
              Laudantium</span
            >
            <span>
              tempora libero pariatur molestiae qui, fugiat eaque, maxime</span
            >
            <span
              >voluptatem ab deserunt nesciunt quasi quas quos ipsam sint,</span
            >
            <span>molestias consequuntur in error.</span>
          </p>

          <div class="border"></div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  name: "HomeView",
  setup() {
    $(document).ready(function () {
      gsap.from(".logo", {
        duration: 2,
        opacity: 0,
        translateX: "-200px",
        ease: Expo.easeInOut,
      });

      gsap.from(".contact", {
        duration: 4,
        opacity: 0,
        translateX: "200px",
        ease: Expo.easeInOut,
      });

      gsap.from(".border", {
        duration: 5,
        opacity: 0,
        scale: 0,
        translateX: "200px",
        ease: Expo.easeInOut,
      });

      gsap.from(".text > p > span", {
        duration: 3,
        opacity: 0,
        scale: 0,
        translateX: "200px",
        ease: Expo.easeInOut,
        stagger: {
          from: "left",
          amount: 3,
          ease: Expo.easeInOut,
        },
      });
    });
  },
};
</script>

<style lang="scss" scoped>
.home {
  background-color: #998c6a;
  height: 100vh;
  padding: 1em 2em;

  header {
    display: flex;
    justify-content: space-between;
    padding-bottom: 1em;
    position: relative;
  }

  main {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;

    .intro {
      padding: 10em;
      font-size: 2em;

      .text {
        padding-bottom: 1em;
        text-align: left;
        position: relative;
      }
    }
  }

  .border {
    position: absolute;
    left: 0;
    bottom: 0;
    height: 2px;
    width: 100%;
    background-color: #fff;
  }
}
</style>
