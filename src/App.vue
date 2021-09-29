<template>
  <Title />
  <Popup @add="addContactHandler" />
  <Contacts :contacts="contacts" @delete="deleteHandler" />
  <p v-if="contacts.length === 0">Контактов нет</p>
</template>

<script>
import Title from "./components/Title.vue";
import Popup from "./components/Popup.vue";
import Contacts from "./components/Contacts.vue";
export default {
  name: "App",
  components: { Title, Contacts, Popup },
  data() {
    return {
      contacts: [],
      contact: {
        name: null,
        phone: null,
        id: Date.now(),
      },
    };
  },
  methods: {
    openPopup() {
      this.contactAddPopup = true;
    },
    addContactHandler(item) {
      this.contacts.push(item);
      this.contactAddPopup = false;
    },
    deleteHandler(id) {
      this.contacts = this.contacts.filter((contact) => contact.id !== id);
    },
  },
};
</script>

<style>
input {
  margin-left: 5px;
}
#app {
  font-family: "Inter", Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
