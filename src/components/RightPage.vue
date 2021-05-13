<template>
  <div
    class="bg-green-400 rounded-tr-xl rounded-br-xl h-full border-r border-gray-500 p-8"
  >
    <div class="space-y-2">
      <div class="space-y-1">
        <h3 class="text-xl">Contacts</h3>
        <div class="flex space-x-2">
          <div><i class="fas fa-home text-white"></i></div>
          <div>
            <div>{{ contact.street }}</div>
            <div>{{ contact.postalCode }} {{ contact.city }}</div>
          </div>
        </div>
        <div class="flex space-x-2">
          <i class="fas fa-phone-alt fas fa-home text-white"></i>
          <p class="">{{ contact.phone }}</p>
        </div>
      </div>
      <div class="flex flex-col">
        <h3 class="text-xl">Hobbies</h3>
        <ul class="pt-0">
          <li v-for="(hobby, index) in contact.hobbies" :key="index">
            <i class="fas fa-arrow-right text-white"></i>
            {{ hobby }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  props: {
    contact: {
      type: [Object, String],
    },
  },
});
</script>

<style scoped>
</style>