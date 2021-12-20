<template>
  <ul>
    <li v-for="(list, index) in lists" :key="index" class="list">
      <the-list :list="list" :index="index" />
    </li>
  </ul>
</template>

<script>
import TheList from "../components/TheList.vue";

export default {
  components: { TheList },
  name: "CreateLists",
  props: ["lists"],
};
</script>

<style scoped>
ul {
  padding: 0 1rem;
}
</style>
