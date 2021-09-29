<template>
  <div class="contact">
    <p>
      {{ contact.name }}:<span>{{ contact.phone }}</span>
    </p>
    <div
      class="button_delete"
      @click.prevent="$emit('delete', contact.id)"
    ></div>
  </div>
</template>

<script>
export default {
  name: "Contact",
  emits: ["delete"],
  props: {
    contact: {
      type: Object,
    },
  },
};
</script>

<style>
.contact {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 7px 0;
}
.button_delete {
  background-image: url(../assets/delete.svg);
  background-repeat: no-repeat;
  background-size: contain;
  width: 15px;
  height: 15px;
}
</style>