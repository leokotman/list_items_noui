<template>
  <div id="app">
    <create-lists :lists="lists" class="create_list" />
    <show-lists :lists="lists" class="show_list" />
  </div>
</template>

<script>
import CreateLists from "./assets/views/CreateLists.vue";
import ShowLists from "./assets/views/ShowLists.vue";

export default {
  name: "App",
  components: { CreateLists, ShowLists },
  data() {
    return {
      lists: [
        {
          title: "List 1",
          items: [
            { name: "Item 1", quantity: 8, color: "#E90804", checked: true },
            { name: "Item 2", quantity: 6, color: "#F4F709", checked: true },
            { name: "Item 3", quantity: 12, color: "#148007", checked: true },
            { name: "Item 4", quantity: 2, color: "#0004FF", checked: false },
          ],
          allChecked: false,
          someChecked: true,
        },
        {
          title: "List 2",
          items: [
            { name: "Item 1", quantity: 7, color: "#0BE904", checked: false },
            { name: "Item 2", quantity: 3, color: "#09D6F6", checked: true },
            { name: "Item 3", quantity: 12, color: "#F66309", checked: false },
            { name: "Item 4", quantity: 3, color: "#4D09F6", checked: false },
          ],
          allChecked: false,
          someChecked: true,
        },
        {
          title: "List 3",
          items: [
            { name: "Item 1", quantity: 2, color: "#0BE904", checked: false },
            { name: "Item 2", quantity: 6, color: "#09D6F6", checked: false },
            { name: "Item 3", quantity: 5, color: "#F66309", checked: false },
            { name: "Item 4", quantity: 3, color: "#4D09F6", checked: false },
            { name: "Item 5", quantity: 1, color: "#F66309", checked: false },
            { name: "Item 6", quantity: 7, color: "#4D09F6", checked: false },
          ],
          allChecked: false,
          someChecked: false,
        },
      ],
    };
  },
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
