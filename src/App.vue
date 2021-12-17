<template>
  <div id="app">
    <create-list :lists="lists" class="create_list" />
    <show-list :lists="lists" class="show_list" />
  </div>
</template>

<script>
import CreateList from "./components/CreateList.vue";
import ShowList from "./components/ShowList.vue";

export default {
  name: "App",
  components: { CreateList, ShowList },
  data() {
    return {
      lists: [
        {
          title: "List 1",
          items: [
            { name: "Item 1", quantity: 10, color: "#E90804", checked: true },
            { name: "Item 2", quantity: 16, color: "#F4F709", checked: true },
            { name: "Item 3", quantity: 40, color: "#148007", checked: true },
            { name: "Item 4", quantity: 0, color: "#0004FF", checked: false },
          ],
          itemsShown: true,
          allChecked: false,
          someChecked: true,
        },
        {
          title: "List 2",
          items: [
            { name: "Item 1", quantity: 20, color: "#0BE904", checked: false },
            { name: "Item 2", quantity: 26, color: "#09D6F6", checked: false },
            { name: "Item 3", quantity: 50, color: "#F66309", checked: false },
            { name: "Item 4", quantity: 0, color: "#4D09F6", checked: false },
          ],
          itemsShown: true,
          allChecked: false,
          someChecked: false,
        },
        {
          title: "List 3",
          items: [],
          itemsShown: true,
          allChecked: false,
          someChecked: false,
        },
      ],
    };
  },
  methods: {},
};
</script>

<style>
#app {
  display: flex;
  flex-wrap: wrap;
}
.create_list,
.show_list {
  list-style-type: none;
  width: 45%;
  border: 1px solid darkblue;
}
</style>
