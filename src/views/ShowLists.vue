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
                v-show="item.checked"
                @click="item.quantity--"
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
ul {
  font-size: 1.2rem;
  line-height: 1.7rem;
  padding: 0 1rem;
}
.list_outcome {
  margin: 1rem 0 1rem;
  padding: 0 1rem .5rem;
  border: 1px solid darkblue;
  box-sizing: border-box;
  border-radius: 3px;
}
.list_outcome label {
  font-size: 1.2rem;
}
.items_outcome {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  justify-content: start;
  row-gap: .8rem;
}
.item_squares {
  display: flex;
  flex-wrap: wrap;
  list-style-type: none;
  gap: 5px;
}
.square {
  min-width: 1rem;
  min-height: 1rem;
}
</style>
