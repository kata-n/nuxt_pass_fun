<template>
  <div class="pass_container">
    <div v-bind:class="backgroundColor">
      <input
        class="input__box"
        v-bind:type="textPass"
        v-model.trim="passwordStrong"
      />
      <p>入力文字数：{{ passwordStrong.length }}文字</p>
      <br />
      <template>
        <div><button type="button">コピーする</button></div>
      </template>
      <br />
      <button type="button" class="show__btn" @click="chageVisible">
        {{ showBtnname }}
      </button>
      <br />
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
      passwordStrong: "",
      passwordmessage: "",
      passwordStrong2: 0
    };
  },
  methods: {
    chageVisible: function() {
      this.showPassword = !this.showPassword;
      this.textPass = this.showPassword ? "text" : "password";
      this.showBtnname = this.showPassword ? "隠す" : "表示する";
    },
    start: function() {
      // @ts-ignore: Unreachable code error
      this.$confetti.start();
    },
    stoping: function() {
      // @ts-ignore: Unreachable code error
      this.$confetti.stop();
    }
  },
  computed: {
    backgroundColor: function(): any {
      //背景の文字列
      if (this.passwordStrong.length > 0) {
        return (this.textColor = `colorLevel_${this.passwordStrong2}`);
      } else {
        this.textColor = "colorLevel_" + `${this.passwordStrong2}`;
      }
    },
    inputPassScore: function() {
      //強力具合を数値化
      let inputpass_score: number = 0;
      this.passwordStrong2 = 0;

      if (this.passwordStrong.length >= 8) {
        inputpass_score += 10;
        this.passwordStrong2 += 10;
      }

      const password_patterns = [
        /\d/, //0-9までのどれかあるか
        /[a-z]/, //小文字アルファベットがあるか
        /[A-Z]/, //大文字アルファベットがあるか
        /\#/, //#を使っているか
        /\!/ //!を使っているか
      ];

      password_patterns.forEach(password_patterns => {
        if (this.passwordStrong.match(password_patterns)) {
          inputpass_score += 5;
          this.passwordStrong2 += 5;
        }
      });

      const error_password_patterns = [
        /[\u3041-\u3096]/, //ひらがながあるか
        /[\u30A1-\u30FA]/ //カタカナあるか
      ];

      error_password_patterns.forEach(error_password_patterns => {
        if (this.passwordStrong.match(error_password_patterns)) {
          console.log("ひらがなorカタカナあるわ");
        }
      });

      //スコア確認
      console.log("スコア確認", inputpass_score);
      console.log("テスト進捗確認", this.passwordStrong2);

      return inputpass_score;
    },
    passResuletmessage: function() {
      const PASSWORD_SCORE = this.inputPassScore;
      let passwordmessage: string = "パスワードを入力してね！！";

      switch (PASSWORD_SCORE) {
        case 5:
          // console.log("まだまだいける");
          passwordmessage = "まだまだいける";
          break;
        case 10:
          // console.log("まだ強くなる");
          passwordmessage = "まだ強くなる";
          break;
        case 15:
          // console.log("ふつうだよ");
          passwordmessage = "ふつうだよ";
          break;
        case 20:
          // console.log("いい感じ！");
          passwordmessage = "いい感じ！";
          break;
        case 25:
          // console.log("いい感じ！");
          passwordmessage = "もう一息！！";
          break;
        case 30:
          passwordmessage = "これでOK！！大丈夫！！";
          break;
        default:
          console.log("計測不能");
      }

      return passwordmessage;
    },
    passwordMessageCss: function(): void {
      const PASSWORD_SCORE: number = 0;

      if (PASSWORD_SCORE >= 50) {
        this.textColor = "score_label_50";
      }
    }
  },
  watch: {
    inputPassScore: {
      handler: function(id, oldId) {
        if (this.inputPassScore === 30) {
          // @ts-ignore: Unreachable code error
          this.$confetti.start();
          setTimeout(() => {
            // @ts-ignore: Unreachable code error
            this.$confetti.stop();
          }, 3000);
        }
      }
    },
    textColor: {
      handler: function(id, oldId) {
        this.$emit("backgroundcolorlevel", this.textColor);
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
  margin: 10px 20px;
  width: 140px;
  padding: 10px;
  background-color: beige;
}
</style>
