<template>
  <div class="grid grid-cols-2">
    <div>
      <LeftPage :avatarLink="avatarLink" :contact="singleContact" />
    </div>
    <div>
      <RightPage :contact="singleContact" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

import LeftPage from "@/components/LeftPage.vue";
import RightPage from "@/components/RightPage.vue";

export default Vue.extend({
  props: {
    contacts: {
      type: [],
    },
    selectedContact: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    avatarLink() {
      if (!this.singleContact) return "";
      return `https://avatars.dicebear.com/api/female/${this.singleContact.firstName}.svg`;
    },
    singleContact() {
      return this.contacts[this.selectedContact];
    },
  },

  components: {
    LeftPage,
    RightPage,
  },
});
</script>

<style scoped>
</style>