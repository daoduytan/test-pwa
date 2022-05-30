<template>
  <div>
    <Tutorial />

    <button @click="thisClick">s</button>
  </div>
</template>

<script>
export default {
  name: "1IndexPage",

  data: {
    test: null,
  },

  methods: {
    handleScroll(e) {
      // Your scroll handling here
      console.log({ e });

      this.test = e;
    },
    thisClick() {
      console.log("dsala", this.test);
    },
  },
  beforeMount() {
    window.addEventListener("beforeinstallprompt", this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener("beforeinstallprompt", this.handleScroll);
  },
};
</script>
