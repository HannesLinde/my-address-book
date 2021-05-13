<template>
  <div>
    <h2 class="text-xl">List</h2>
    <ListOverview :contacts="contacts" :selectedContact="selectedContact" />

    <div class="max-w-screen-sm h-100 mx-auto">
      <div class="relative">
        <div
          class="absolute right-0 bottom-0 p-2 cursor-pointer bg-gray-400 rounded-br-xl rounded-tl-xl"
          @click="next"
        >
          <i class="fas fa-arrow-right"></i>
        </div>
        <div
          class="absolute right-0 top-0 p-2 cursor-pointer bg-gray-800 text-white rounded-bl-xl rounded-tr-xl"
        >
          <i class="far fa-list-alt"></i>
        </div>
        <div
          class="absolute left-0 top-0 p-2 cursor-pointer bg-gray-400 rounded-br-xl rounded-tl-xl"
          @click="previous"
        >
          <i class="fas fa-arrow-left"></i>
        </div>
        <div
          class="absolute left-0 bottom-0 p-2 cursor-pointer bg-gray-800 text-white rounded-tr-xl rounded-bl-xl"
        >
          <i class="fas fa-plus"></i>
        </div>
        <div class="grid grid-cols-2">
          <div>
            <LeftPage :avatarLink="avatarLink" :contact="singleContact" />
          </div>
          <div>
            <RightPage :contact="singleContact" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";

import LeftPage from "@/components/LeftPage.vue";
import RightPage from "@/components/RightPage.vue";
import ListOverview from "./ListOverview.vue";

export default Vue.extend({
  data() {
    return {
      contacts: [],
      selectedContact: 0,
      showList: false,
    };
  },
  computed: {
    avatarLink() {
      return `https://avatars.dicebear.com/api/female/${this.singleContact.firstName}.svg`;
    },
    singleContact() {
      return this.contacts[this.selectedContact];
    },
  },
  async mounted() {
    try {
      const response = await axios.get("http://localhost:3000/contacts");
      this.contacts = response.data;
    } catch (error) {
      console.log(error);
    }
  },
  methods: {
    next() {
      if (this.selectedContact == this.contacts.length - 1) {
        this.selectedContact = 0;
      } else {
        this.selectedContact += 1;
      }
    },
    previous() {
      if (this.selectedContact == 0) {
        this.selectedContact = this.contacts.length - 1;
      } else {
        this.selectedContact -= 1;
      }
    },
  },
  components: {
    LeftPage,
    RightPage,
    ListOverview,
  },
});
</script>

<style scoped>
</style>