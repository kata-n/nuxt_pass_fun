<template>
  <div class="container">
    <div class="pass-field">
      <Logo />
      <client-only>
        <inputmaking-box />
      </client-only>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import InputmakingBox from "@/components/InputmakingBox.vue";

export default Vue.extend({
  components: {
    InputmakingBox
  },
  methods: {
    backgroundcolorlevel() {}
  }
});
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  min-height: 100vh;
  max-width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-image: linear-gradient(to right, #2af598 0%, #009efd 100%);
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.pass-field {
  width: 80%;
  margin: 40px auto;
  padding: 40px;
  background-color: rgba(255, 255, 255, 0.2);
}
</style>
