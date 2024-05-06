<template>
  <div>
    <h1>My ToDo</h1>
    <h3>{{ completedAll }}</h3>

    <!-- Show List -->
    <ItemList :items="DataItemList" @change-item="CompletedItem"></ItemList>
  </div>
</template>

<script setup lang="ts">
// Import the item interface
import type { ItemInterface } from './models/items/item.interface';

// Import the item list component
import ItemList from './components/items/items.component.vue';

// Import reactive and computed from vue
import { reactive, computed } from 'vue';

// Create data for item list
const DataItemList: ItemInterface[] = reactive([
  {
    id: 1,
    name: 'coffee',
    completed: true,
  },
  {
    id: 2,
    name: 'books',
    completed: false,
  },
]);

// Define function to handle completed items
const CompletedItem = (id: number) => {
  alert("Id Item" + id);
};

// Compute the completion status of all items
const completedAll = computed(() => {
  let all = DataItemList.length;
  let countCompleted = 0;

  DataItemList.forEach(element => {
    if (element.completed) {
      countCompleted++;
    }
  });

  return countCompleted === all ? "All todo is completed" : "No";
});
</script>
