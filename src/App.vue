<template>
  <main>
    <div class="row">
      <div class="col">
        selected {{ selectedLeft.length }}/{{ itemsLeft.length }}:
        <br>

        <ul>
          <li
            v-for="(item, key) in selectedLeft"
            :key="key"
          >{{ item.name }}</li>
        </ul>
      </div>
      <div class="col">
        selected item
        <br>

        {{ selectedRight?.name }}
      </div>
    </div>
    <div class="row">
      <div class="col">
        <div class="d-flex flex-column">
          <label
            v-for="item in itemsLeft"
            :key="item.id"
          >
            <input
              :value="item"
              type="checkbox"
              name="itemsLeft"
              v-model="selectedLeft"
            >
            {{ item.name }}
          </label>
        </div>
      </div>
      <div class="col">
        <div class="d-flex flex-column">
          <label
            v-for="item in itemsRight"
            :key="item.id"
          >
            <input
              :value="item"
              type="radio"
              name="itemsRight"
              v-model="selectedRight"
            >
            {{ item.name }}
          </label>
        </div>
      </div>
    </div>
  </main>
</template>

<script lang="ts" setup>
import {
  itemsLeft,
  itemsRight,
  type ListItem
} from "@/constants/itemsList.ts"
import { ref } from "vue";

const selectedLeft = ref<ListItem[]>([])
const selectedRight = ref<ListItem>()
</script>

<style scoped lang="scss">
$gap: 30px;

main {
  display: flex;
  flex-direction: column;
  row-gap: $gap;
}

.row {
  display: flex;
  gap: $gap;
  max-width: 100%;
}

.col {
  border: 1px solid #333;
  flex-shrink: 0;
  flex-grow: 1;
  padding: 5px 10px;
  flex-basis: 0;
}

.d-flex {
  display: flex;
}

.flex-column {
  flex-direction: column;
}
</style>
