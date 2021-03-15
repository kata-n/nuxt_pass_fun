<template>
  <div>
    <input ref="inputPassword" class="input__box" type="text" />
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
      inputPassword: "",
      showPassword: false
    };
  },
  methods: {
    chageVisible: function() {
      this.showPassword = !this.showPassword;
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
