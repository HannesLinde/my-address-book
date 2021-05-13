<template>
  <div
    class="bg-green-400 rounded-tl-xl rounded-bl-xl h-full border-r border-gray-500 p-8 flex flex-col place-items-center space-y-2"
  >
    <img :src="avatarLink" class="w-40 h-40 rounded-full" />
    <h2 class="text-xl leading-tight">
      {{ contact.firstName }}<br />
      {{ contact.lastName }}
    </h2>
    <p>Born {{ new Date(contact.dateOfBirth).toLocaleDateString() }}</p>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  props: {
    avatarLink: {
      type: String,
      default: "",
    },
    contact: {
      type: Object,
    },
  },
});
</script>

<style scoped>
</style>