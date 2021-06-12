<script lang="ts">
import Vue from "vue";
// Uncomment import and local "components" registration if library is not registered globally.
import { SingleInput } from "@/entry.esm";

export default Vue.extend({
  name: "ServeDev",

  components: {
    SingleInput,
  },

  data() {
    return {
      fullMpin: "",
    };
  },
});
</script>

<template>
  <div id="app">
    <SingleInput
      v-model="fullMpin"
      formId="id"
      :boxCount="6"
      textColor="green"
      borderColor="blue"
      textSize="2em"
      :withBorder="true"
      borderRadius="10%"
      backgroundColor="#0ffacf"
      type="text"
    />
  </div>
</template>
