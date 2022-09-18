<template>
  <nav>
    <div class="cursor-app"></div>
    <router-view />
  </nav>
</template>

<script>
import { onMounted } from "vue";
import {  useRouter } from "vue-router";
//.
export default {
  setup() {
    const router = useRouter();
    //.
    onMounted(function () {
      const persistance = localStorage.getItem("persistance");
      if (persistance) router.push("enter");
      router.push("enter");
    });

    $(document).ready(function () {
      $(document).on("mousemove", function (e) {
        $(".cursor-app").css({
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
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Text+Me+One&display=swap");

body {
  overflow-x: hidden;
  font-family: "Text Me One", sans-serif;
  color: #ffffff;
  text-transform: uppercase;
  margin: 0;
  padding: 0;
  // cursor: none;
  user-select: none;
  background-color: #000;
}

* {
  margin: 0;
  padding: 0;
}

::-webkit-scrollbar {
  display: none;
}
</style>
