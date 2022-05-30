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
      this.test.prompt();

      // Wait for the user to respond to the prompt
      this.test.userChoice.then((choiceResult) => {
        if (choiceResult.outcome === "accepted") {
          console.log("User accepted the A2HS prompt");
        } else {
          console.log("User dismissed the A2HS prompt");
        }
        this.test = null;
      });

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
