<template>
  <div>
    <input class="input__box" type="text" />
    <p>testings</p>
    <p>secondtestings</p>
  </div>
</template>

<script lang="ts">
//type scriptはvueをimportしないといけない
import Vue from "vue";

export default Vue.extend({
  name: "InputmakingBox"
});
</script>

<style>
.input__box {
  padding: 10px;
}
</style>
