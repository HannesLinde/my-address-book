<template>
  <div class="max-w-screen-sm mx-auto bg-blue-300 rounded-xl pt-12 relative">
    <div class="flex flex-col place-items-center">
      <input
        type="text"
        placeholder="Search for first or last name"
        class="absolute top-0 text-sm p-1"
      />
    </div>
    <div
      class="p-2 border-t border-grey-400 flex justify-between"
      v-for="contact in contacts"
      :key="contact.id"
      @click="$emit('select:name', (selectedContact = contact.id - 1))"
    >
      <div class="cursor-pointer">
        {{ contact.firstName }} {{ contact.lastName }}
      </div>
      <div><i class="fas fa-user-edit"></i></div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  props: {
    contacts: {
      type: [Array],
    },
    selectedContact: {
      type: Number,
    },
  },
  /* methods: {
    selectName() {
      this.selectedContact = this.contact.id;
    },
  }, */
});
</script>

<style scoped>
</style>