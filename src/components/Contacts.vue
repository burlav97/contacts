<template>
  <div class="contacts__container">
    <Contact
      :contact="contact"
      v-for="contact in contacts"
      :key="contact.id"
      @delete="handleDelete"
    />
  </div>
</template>

<script >
import Contact from "./Contact.vue";
export default {
  name: "Contacts",
  props: ["contacts"],
  methods: {
    handleDelete(id) {
      this.$emit("delete", id);
    },
  },
  components: { Contact },
};
</script>

<style scoped>
.contacts__container {
  max-width: 30%;
  margin: 0 auto;
}
</style>
