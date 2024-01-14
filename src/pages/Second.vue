<template>
  <q-page padding>
    <h6>This is Second page</h6>
    <q-btn
      class="q-mb-md"
      color="primary"
      label="Show Q Object"
      @click="showQ"
    />
    <p v-for="post in posts" :key="post.id">{{ post.title }}</p>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import { api } from "src/boot/axios";
export default defineComponent({
  name: "SecondPage",
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    showQ() {
      console.log(this.$q);
    },
  },
  async mounted() {
    console.log("Component is mounted");
    const { data } = await api.get();
    this.posts = data;
  },
  created() {
    console.log("Component is created");
  },
});
</script>
