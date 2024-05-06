<template>
    <div>Item List</div>
    <!---show Items--->
    <ul 
    v-for="data in items" :key="data.id">
    <li>{{ data.name }} - <input type="checkbox" v-model="data.completed"
        @click="completedItems(data.id)"></li>
</ul>
{{ items }}
</template>
<script setup lang="ts">

//import type interface item

import type { ItemInterface } from '../../models/items/item.interface';
//define prop data

defineProps<{items: ItemInterface[]}>();

//Emit FN
const emit = defineEmits<{(e:'changeItem',id:number): any }>();

//function completed items
const completedItems = (id) =>{
    //test id item 1
   emit('changeItem', id);
};
</script>