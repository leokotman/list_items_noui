<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <create-list :lists="lists" />
    <show-list :lists="lists" />
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
            { name: "Item 1", quantity: 0, color: "#0004FF", checked: false },
          ],
          allChecked: false,
          someChecked: true,
        },
        {
          title: "List 2",
          items: [
            { name: "Item 1", quantity: 20, color: "#0BE904", checked: false },
            { name: "Item 2", quantity: 26, color: "#09D6F6", checked: false },
            { name: "Item 3", quantity: 50, color: "#F66309", checked: false },
            { name: "Item 1", quantity: 0, color: "#4D09F6", checked: false },
          ],
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
}
</style>
