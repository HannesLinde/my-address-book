<template>
  <div>
    <div
      v-if="!contacts.length == 0"
      class="max-w-screen-sm h-100 mx-auto relative"
    >
      <ListOverview
        v-if="showList"
        :contacts="contacts"
        :selectedContact="selectedContact"
        @select:name="
          selectedContact = $event;
          showList = false;
        "
      />
      <ContactPage
        v-if="!showList"
        :contacts="contacts"
        :selectedContact="selectedContact"
      />
      <div
        class="absolute left-0 top-0 p-2 cursor-pointer bg-gray-800 text-white rounded-br-xl rounded-tl-xl"
      >
        <i class="fas fa-plus"></i>
      </div>
      <div
        class="absolute right-0 top-0 p-2 cursor-pointer bg-gray-800 text-white rounded-bl-xl rounded-tr-xl"
        @click="showList = !showList"
      >
        <i class="far fa-list-alt"></i>
      </div>

      <div
        v-if="!showList"
        class="absolute right-0 bottom-0 p-2 cursor-pointer bg-gray-400 rounded-br-xl rounded-tl-xl"
        @click="next"
      >
        <i class="fas fa-arrow-right"></i>
      </div>

      <div
        v-if="!showList"
        class="absolute left-0 bottom-0 p-2 cursor-pointer bg-gray-400 rounded-tr-xl rounded-bl-xl"
        @click="previous"
      >
        <i class="fas fa-arrow-left"></i>
      </div>
    </div>
    <Loadingspinner v-if="contacts.length == 0" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";
import ContactPage from "../components/ContactPage.vue";
import ListOverview from "@/components/ListOverview.vue";
import Loadingspinner from "@/components/Loadingspinner.vue";

export default Vue.extend({
  data() {
    return {
      showList: false,
      contacts: [],
      selectedContact: 0,
    };
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
    ContactPage,
    ListOverview,
    Loadingspinner,
  },
});
</script>

<style scoped>
</style>