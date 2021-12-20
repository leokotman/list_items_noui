<template>
  <div>
    <img
      src="../assets/img/icons8-expand-arrow-50.png"
      :class="'list_arrow' + (!list.itemsShown ? ' list_arrow-closed' : '')"
      @click="list.itemsShown = !list.itemsShown"
    />
    <label :for="list.title + '_' + index">
      <input
        type="checkbox"
        :id="list.title + '_' + index"
        v-model="allChecked"
      />
      {{ list.title }}
    </label>
    <ul class="items_list" v-show="list.itemsShown">
      <li v-for="(item, i) in list.items" :key="i">
        <label
          :for="item.name + '_' + index + '_' + i"
          @click="countCheckedItems()"
        >
          <input
            type="checkbox"
            :id="item.name + '_' + index + '_' + i"
            v-model="item.checked"
            @change="countCheckedItems()"
          />
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
  </div>
</template>

<script>
export default {
  props: ["list", "index"],
  data() {
    return {
      allChecked: false,
      selectedItems: [],
    };
  },
  methods: {
    selectAll() {
      if (this.list.allChecked) {
        // this.allChecked = true;
        const selected = this.list.items.forEach((item) => {
          return (item.checked = true);
        });
        console.log("selectAll allChecked worked");
        this.list.someChecked = false;
        this.selectedItems = selected;
      } else if (this.list.someChecked) {
        console.log("selectAll someChecked worked");
      } else {
        // this.allChecked = false;
        this.selectedItems = [];
        this.list.items.forEach((item) => {
          return (item.checked = false);
        });
      }
    },
    countCheckedItems() {
      let checkedItemsArr = this.list.items.filter(
        (item) => item.checked == true
      );
      if (checkedItemsArr.length === this.list.items.length) {
        console.log("allChecked = true");
        return (this.allChecked = true);
      } else if (checkedItemsArr.length > 0) {
        console.log("list.someChecked = true");
        return (this.list.someChecked = true), (this.allChecked = false);
      } else {
        console.log("allChecked = false");
        return (this.allChecked = false), (this.list.someChecked = false);
      }
    },
  },
  watch: {
    allChecked() {
      this.list.allChecked = !this.list.allChecked;
      this.selectAll();
    },
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
