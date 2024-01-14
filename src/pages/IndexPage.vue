<template>
  <q-banner v-if="isSent" rounded class="bg-red-4 text-white q-mt-md">
    <q-btn color="primary" icon="check" label="Added" @click="closeBanner" />
  </q-banner>
  <q-page class="flex flex-center column justify-around">
    <q-input
      type="text"
      label="Your name"
      placeholder="Please enter your name"
      v-model="name"
      :error="name.length < 3"
      error-message="Name length < 3"
      shadow-text
      debounce="300"
      maxlength="10"
      outlined
      rounded
    />
    <div class="cursor-pointer rounded-borders">
      <h3>{{ name }}</h3>
      <q-btn
        color="primary"
        :loading="name !== '' && name.length < 3"
        push
        padding="30px"
        rounded
        size="24px"
        @click="showAlert"
        >Add</q-btn
      >
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  data() {
    return {
      name: "",
      isSent: false,
    };
  },
  methods: {
    showAlert() {
      this.isSent = true;
    },
    closeBanner() {
      this.isSent = false;
    },
  },
});
</script>
