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
    {{ fullMpin }}
    <SingleInput
      v-model="fullMpin"
      formId="id"
      :boxCount="4"
      textColor="green"
      borderColor="red"
      textSize="2em"
      :withBorder="false"
      borderRadius="0%"
      backgroundColor="none"
    />
  </div>
</template>
