<template>
  <ul>
    <li v-for="(list, i) in lists" :key="i" class="list">
      <img
        src="../assets/img/icons8-expand-arrow-50.png"
        :class="'list_arrow' + (!list.itemsShown ? ' list_arrow-closed' : '')"
        @click="list.itemsShown = !list.itemsShown"
      />
      <label :for="list.title + '_' + i">
        <input
          type="checkbox"
          :id="list.title + '_' + i"
        />
        {{ list.title }}
      </label>
      <ul class="items_list" v-show="list.itemsShown">
        <li v-for="(item, i) in list.items" :key="i">
          <input
            type="checkbox"
            :id="item.name + '_' + i"
            v-model="item.checked"
          />
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
  methods: {
    toggleListChecked() {
      this.lists.forEach((list) => {
        let checkedItems = list.items.filter((item) => {
          return item.checked === true;
        });
        if (checkedItems.length === list.items.length) {
          this.checkAllItems(list);
        } else if (
          checkedItems.length !== list.items.length &&
          checkedItems.length > 0
        ) {
          return (list.someChecked = true), (list.allChecked = false);
        } else if (checkedItems.length === 0) {
          return (list.someChecked = false), (list.allChecked = false);
        }
      });
      console.log("toggleList in createList worked");
    },
    checkAllItems(list) {
      if (list.allChecked === true) {
        list.allChecked = false;
        console.log("list.allChecked = false");
        for (let i = 0; i < list.items.length; i++) {
          if (list.items[i].checked === true) {
            list.items[i].checked = false;
          }
          console.log("list[i]" + list.items[i]);
        }
        // list.forEach((item) => {
        //   return (item.checked = false);
        // });
      } else if (list.allChecked === false) {
        list.allChecked = true;
        console.log("list.allChecked = true");
        for (let i = 0; i < list.items.length; i++) {
          if (list.items[i].checked === false) {
            list.items[i].checked = true;
          }
          console.log("list[i]" + list.items[i]);
        }
        // list.forEach((item) => {
        //   return (item.checked = true);
        // });
      }
    },
  },
  created() {
    this.toggleListChecked();
  },
  beforeUpdate() {
    this.toggleListChecked();
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
