<template>
  <div>
    <input class="input__box" v-bind:type="textPass" ref="passwordStrong" />
    <br />
    <button type="button" class="show__btn" @click="chageVisible">
      {{ showBtnname }}
    </button>
    <div>{{ textPass.length }}</div>
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
      showPassword: false,
      showBtnname: "隠す"
    };
  },
  methods: {
    chageVisible: function() {
      this.showPassword = !this.showPassword;
      this.textPass = this.showPassword ? "text" : "password";
      this.showBtnname = this.showPassword ? "隠す" : "表示する";
    }
  },
  computed: {}
});
</script>

<style>
.input__box {
  margin-top: 10px;
  padding: 10px;
}
.show__btn {
  margin: 20px;
  width: 140px;
  padding: 10px;
}
</style>
