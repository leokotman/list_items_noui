<template>
  <section>
    <img
      src="../assets/img/icons8-expand-arrow-50.png"
      :class="'list_arrow' + (!itemsShown ? ' list_arrow-closed' : '')"
      @click="itemsShown = !itemsShown"
    />
    <label :for="list.title + '_' + index" class="container">
      <input
        type="checkbox"
        :id="list.title + '_' + index"
        v-model="allChecked"
        :class="checkBoxClass"
      />
      <span class="checkmark"></span>
      {{ list.title }}
    </label>
    <ul class="items_list" v-show="itemsShown">
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
  </section>
</template>

<script>
export default {
  props: ["list", "index"],
  data() {
    return {
      allChecked: false,
      selectedItems: [],
      someChecked: false,
      itemsShown: false,
    };
  },
  methods: {
    selectAll() {
      if (this.allChecked) {
        const selected = this.list.items.forEach((item) => {
          return (item.checked = true);
        });
        console.log("selectAll allChecked worked");
        this.someChecked = false;
        this.selectedItems = selected;
      } else if (this.someChecked) {
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
      if (
        checkedItemsArr.length === this.list.items.length &&
        this.list.items.length > 0
      ) {
        console.log("allChecked = true");
        return (this.allChecked = true);
      } else if (checkedItemsArr.length > 0) {
        console.log("list.someChecked = true");
        return (this.someChecked = true), (this.allChecked = false);
      } else {
        console.log("allChecked = false");
        return (this.allChecked = false), (this.someChecked = false);
      }
    },
    countItemsInList() {
      if (this.list.items.length > 0) {
        return (this.itemsShown = true);
      } else {
        return (this.itemsShown = false);
      }
    },
  },
  computed: {
    checkBoxClass: function () {
      if (this.someChecked) {
        return "someChecked";
      } else if (this.allChecked) {
        return "allChecked";
      } else {
        return "notChecked";
      }
    },
  },
  watch: {
    allChecked() {
      this.list.allChecked = !this.list.allChecked;
      this.selectAll();
    },
    someChecked() {
      this.list.someChecked = this.someChecked;
    },
  },
  created() {
    this.countCheckedItems();
    this.countItemsInList();
  },
};
</script>

<style scoped>
section {
  margin: 1rem 0 1rem;
}

.container {
  display: inline-block;
  position: relative;
  padding-left: 2rem;
  margin-left: 1rem;
  margin-bottom: 0.8rem;
  cursor: pointer;
  font-size: 1.2rem;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #eee;
  border-radius: 5px;
}

/* On mouse-over, add a grey background color */
.container:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark,
.container input.someChecked ~ .checkmark {
  background-color: #2196f3;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}
/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the someChecked indicator */
.container input.someChecked ~ .checkmark:after {
  display: block;
  left: 8px;
  top: 8px;
  border: solid white;
  border-width: 5px;
  border-radius: 50%;
}
/* Style the allChecked indicator */
.container input.allChecked ~ .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}

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
