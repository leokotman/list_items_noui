<template>
  <ul>
    <li v-for="(list, i) in lists" :key="i" class="list">
      <img
        src="../assets/img/icons8-expand-arrow-50.png"
        :class="'list_arrow' + (!list.itemsShown ? ' list_arrow-closed' : '')"
        @click="list.itemsShown = !list.itemsShown"
      />
      <label :for="list.title + '_' + i">
        <input type="checkbox" :id="list.title + '_' + i" />
        {{ list.title }}
      </label>
      <ul class="items_list" v-show="list.itemsShown">
        <li v-for="(item, i) in list.items" :key="i">
          <input type="checkbox" :id="item.name + '_' + i" />
          <label :for="item.name + '_' + i">
            {{ item.name }}
          </label>
          <input
            type="number"
            min="0"
            v-model.number="item.quantity"
            class="item_number"
          />
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
  data() {
    return {};
  },
};
</script>

<style scoped>
.items_list {
  list-style-type: none;
}
.list_arrow {
  width: 20px;
}
.list_arrow-closed {
  transform: rotate(-90deg);
}
.item_number {
  width: 2rem;
}
</style>
