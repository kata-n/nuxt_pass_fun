<template>
  <div class="pass_container">
    <div v-bind:class="passScore">
      <input
        class="input__box"
        v-bind:type="textPass"
        v-model.trim="passwordStrong"
      />
      <div>{{ passwordStrong.length }}</div>
      <br />
      <button type="button" class="show__btn" @click="chageVisible">
        {{ showBtnname }}
      </button>
      <p :class="passwordMessageCss" v-text="passResuletmessage"></p>
    </div>
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
      textColor: "colorLevel_0",
      showPassword: false,
      showBtnname: "隠す",
      passwordStrong: ""
    };
  },
  methods: {
    chageVisible: function() {
      this.showPassword = !this.showPassword;
      this.textPass = this.showPassword ? "text" : "password";
      this.showBtnname = this.showPassword ? "隠す" : "表示する";
    }
  },
  computed: {
    passScore: function(): any {
      if (this.passwordStrong.length > 0) {
        return (this.textColor = `colorLevel_${this.passwordStrong.length}`);
      } else {
        this.textColor = "colorLevel_" + `${this.passwordStrong.length}`;
      }
    }
  }
});
</script>

<style lang="scss" scoped>
.pass_container {
  width: 100%;
}
.input__box {
  margin-top: 10px;
  padding: 10px;
}
.show__btn {
  margin: 20px;
  width: 140px;
  padding: 10px;
}
//色を変える
.colorLevel_ {
  &1 {
    background-color: #e0f7fa;
  }
  &2 {
    background-color: #b2ebf2;
  }
  &3 {
    background-color: #80deea;
  }
}
</style>
