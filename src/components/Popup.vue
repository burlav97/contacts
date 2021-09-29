<template>
  <div class="popup">
    <div class="popup__container">
      <form @submit.prevent="addContactHandler(contact)">
        <div class="input">
          <label for="name">Имя</label
          ><input
            type="text"
            id="name"
            placeholder="Введите имя"
            v-model="contact.name"
          />
        </div>
        <div class="input">
          <label for="name">Номер</label
          ><input
            type="number"
            id="name"
            placeholder="Введите телефон"
            v-model="contact.phone"
          />
        </div>
        <button class="button" type="submit">Сохранить</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Popup",
  emits: ["add"],
  props: {
    modal: {
      type: Boolean,
    },
  },
  data() {
    return {
      contacts: [],
      contact: {
        name: null,
        phone: null,
      },
    };
  },
  methods: {
    addContactHandler() {
      const newContact = {
        name: this.contact.name,
        phone: this.contact.phone,
        id: Date.now(),
      };
      this.$emit("add", newContact);
      this.contact = {};
    },
  },
};
</script>

<style>
.popup__container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  background-color: #fff;
  padding: 16px;
  border-radius: 10px;
  box-shadow: 0px 0px 25px rgba(0, 0, 0, 0.15);
  position: relative;
}
.input {
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}
.button {
  background-color: #000;
  border-radius: 5px;
  padding: 4px;
  color: #fff;
  border: 0;
}
</style>