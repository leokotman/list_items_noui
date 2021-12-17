<template>
  <ul>
    <li v-for="(list, i) in lists" :key="i">
      <label>
        {{ list.title }}
        <input type="checkbox" />
      </label>
      <ul>
        <li v-for="(item, i) in list.items" :key="i">
          <input type="checkbox" :id="item.id" />
          <label :for="item.id">
            {{ item.name }}
          </label>
          {{ item.quantity }}
          <input type="color" v-model="item.color" />
        </li>
      </ul>
    </li>
  </ul>
</template>

<script>
export default {
  name: "CreateList",
  props: ["lists"],
};
</script>

<style scoped></style>
