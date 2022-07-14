<template lang="pug">
div
  input.form-control.mb-2(:id="'input-'+slug" v-model="input" @input="outputOndevice = log(kana.getFurigana())")
  // input.form-control.mb-2(v-model="output")
  input.form-control.mb-2(v-model="outputOndevice")
</template>

<script lang="ts">
let slugCount = 1;
</script>

<script setup lang="ts">
// import axios from "axios";
import * as Autokana from "vanilla-autokana";
const input = ref("");
const output = ref("");
const outputOndevice = ref("");
const kana = ref<Autokana.AutoKana>();
const slug = slugCount++;
function log(e) {
  console.log(e);
  return e;
}
onMounted(() => {
  kana.value = Autokana.bind("#input-" + slug);
  console.log(kana);
});
// let timeoutId: number;
// watch(input, () => {
//   if (timeoutId) clearTimeout(timeoutId);
//   setTimeout(async () => {
//     if (input.value) {
//       const result = await axios.post("https://labs.goo.ne.jp/api/hiragana", {
//         app_id:
//           "b500eb0d3d02972909df6ed8d44cfe438e96644babaecdc4a59b8f7353c930ae",
//         sentence: input.value,
//         output_type: "hiragana",
//       });
//       output.value = result.data.converted;
//     } else {
//       output.value = "";
//     }
//   }, 500);
// });

// b500eb0d3d02972909df6ed8d44cfe438e96644babaecdc4a59b8f7353c930ae gooらぼAPPID:非営利
// dj00aiZpPTR4clY2cXR3ZGllVCZzPWNvbnN1bWVyc2VjcmV0Jng9OWQ- yahoo id
</script>
