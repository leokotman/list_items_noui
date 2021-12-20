<template>
  <ul>
    <li v-for="(list, index) in lists" :key="index" class="list">
      <the-list :list="list" :index="index" />
    </li>
  </ul>
</template>

<script>
import TheList from "../../components/TheList.vue";

export default {
  components: { TheList },
  name: "CreateLists",
  props: ["lists"],
  data() {
    return {};
  },
};
</script>

<style scoped></style>
