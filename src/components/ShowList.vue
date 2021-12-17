<template>
  <ul>
    <li v-for="(list, i) in lists" :key="i" class="list_outcome">
      {{ list.title }}
      <ul class="items_outcome">
        <li v-for="(item, i) in list.items" :key="i">
          <ul class="item_squares">
            <li v-for="(square, i) in item.quantity" :key="i">
              <div
                :style="'background-color: ' + item.color + ';'"
                class="square"
              ></div>
            </li>
          </ul>
        </li>
      </ul>
    </li>
  </ul>
</template>

<script>
export default {
  props: ["lists"],
};
</script>

<style scoped>
.items_outcome {
  list-style-type: none;
}
.item_squares {
  display: flex;
  flex-wrap: wrap;
  list-style-type: none;
  gap: 5px;
}
.square {
  min-width: 30px;
  min-height: 30px;
}
</style>
