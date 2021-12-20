<template>
  <div id="app">
    <create-lists :lists="lists" class="create_lists" />
    <show-lists :lists="lists" class="show_lists" />
  </div>
</template>

<script>
import CreateLists from "./views/CreateLists.vue";
import ShowLists from "./views/ShowLists.vue";

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
            { name: "Item 1", quantity: 2, color: "#e801f9", checked: false },
            { name: "Item 2", quantity: 6, color: "#09D6F6", checked: false },
            { name: "Item 3", quantity: 5, color: "#5cf609", checked: false },
            { name: "Item 4", quantity: 3, color: "#4D09F6", checked: false },
            { name: "Item 5", quantity: 1, color: "#fff705", checked: false },
            { name: "Item 6", quantity: 7, color: "#e7e7e7", checked: false },
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
  justify-content: space-evenly;
  align-items: baseline;
}
.create_lists,
.show_lists {
  list-style-type: none;
  width: 45%;
  border: 1px solid darkblue;
  box-sizing: border-box;
}
</style>
