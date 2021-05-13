<template>
  <div>
    <div
      class="bg-blue-300 p-2 border-b border-black"
      v-for="(contact, index) in contacts"
      :key="contact.id"
      @click="selectedContact = index"
    >
      <span>{{ contact.firstName }}</span>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  props: {
    contacts: {
      type: [],
    },
    selectedContact: {
      type: Number,
    },
  },
});
</script>

<style scoped>
</style>