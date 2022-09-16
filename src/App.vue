<template>
  <nav>
    <div class="cursor"></div>
    <router-view />
  </nav>
</template>

<script>
import { onMounted } from "vue";
import { useRouter } from "vue-router";
//.
export default {
  setup() {
    const router = useRouter();
    //.
    onMounted(function () {
      const persistance = localStorage.getItem("persistance");
      if (persistance) return;
      router.push("enter");
    });

    $(document).ready(function () {
      $(document).on("mousemove", function (e) {
        $(".cursor").css({
          width: "30px",
          height: "30px",
          position: "absolute",
          top: e.clientY,
          left: e.clientX,
          translate: "-50% -50%",
          transition: "100ms",
          "border-radius": "50%",
          "background-color": "#fff",
        });
      });
    });
  },
};
</script>

<style lang="scss">
@import url(https://fonts.googleapis.com/css?family=Orbitron:regular,500,600,700,800,900);

body {
  overflow: hidden;
  font-weight: 100;
  font-family: "Orbitron";
  color: #ffffff;
  text-transform: uppercase;
  margin: 0;
  padding: 0;
  cursor: none;
  user-select: none;
}

* {
  margin: 0;
  padding: 0;
}
</style>
