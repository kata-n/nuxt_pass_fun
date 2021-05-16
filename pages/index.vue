<template>
  <div class="container" v-bind:class="backgroundColor">
    <div class="pass-field w-24 min-w-full">
      <Logo />
      <client-only>
        <InputmakingBox @backgroundcolorlevel="changeColor" />
      </client-only>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import InputmakingBox from "@/components/InputmakingBox.vue";

export default Vue.extend({
  data() {
    return {
      backgroundColor: ""
    };
  },
  components: {
    InputmakingBox
  },
  methods: {
    changeColor(message: any) {
      this.backgroundColor = message;
    }
  }
});
</script>

<style lang="scss" scoped>
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
  background-image: linear-gradient(to right, #a8edea 0%, #fed6e3 100%);
  transition: 0.5s;
}

//色を変える
.colorLevel_ {
  &5 {
    background-image: linear-gradient(to right, #5ee7df 0%, #b490ca 100%);
  }
  &10 {
    background-image: linear-gradient(to right, #5ee7df 0%, #b490ca 100%);
    transition: 0.2s;
  }
  &15 {
    background-image: linear-gradient(to right, #96fbc4 0%, #f9f586 100%);
    transition: 0.2s;
  }
  &20 {
    background-image: linear-gradient(to right, #ff5858 0%, #f09819 100%);
    transition: 0.2s;
  }
  &25 {
    background-image: linear-gradient(to right, #a1c4fd 0%, #c2e9fb 100%);
    transition: 0.2s;
  }
  &30 {
    background-image: linear-gradient(to right, #f6d365 0%, #fda085 100%);
    transition: 0.2s;
  }
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
  min-height: 80%;
}

@media screen and (max-width: 420px) {
}
</style>
