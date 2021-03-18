<template>
  <div>
    <input class="input__box" v-bind:type="textPass" />
    <button type="button" @click="chageVisible">表示切り替え</button>
  </div>
</template>

<script lang="ts">
//type scriptはvueをimportしないといけない
import Vue from "vue";

export default Vue.extend({
  name: "InputmakingBox",
  data() {
    return {
      textPass: "text",
      showPassword: false
    };
  },
  methods: {
    chageVisible: function() {
      this.showPassword = !this.showPassword;
      this.textPass = this.showPassword ? "text" : "password";
    }
  }
});
</script>

<style>
.input__box {
  margin-top: 10px;
  padding: 10px;
}
</style>
