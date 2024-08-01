<script setup>

const emit = defineEmits(['filter']);
const filter = (e) => {
    emit('filter', e.target.value);
};
</script>

<template>
    <label class="flex mr-4 items-center flex-nowrap">
          <input type="radio" name="show" value="all" checked @change="filter">
          <span class="whitespace-nowrap ml-1">Show all</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
          <input type="radio" name="show" value="comedy" @change="filter">
          <span class="whitespace-nowrap ml-1">Comedy</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
          <input type="radio" name="show" value="family" @change="filter">
          <span class="whitespace-nowrap ml-1">Family</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
          <input type="radio" name="show" value="action" @change="filter">
          <span class="whitespace-nowrap ml-1">Action</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
          <input type="radio" name="show" value="adventure" @change="filter">
          <span class="whitespace-nowrap ml-1">Adventure</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
          <input type="radio" name="show" value="drama" @change="filter">
          <span class="whitespace-nowrap ml-1">Drama</span>
    </label>
    <label class="flex mr-4 items-center flex-nowrap">
          <input type="radio" name="show" value="short" @change="filter">
          <span class="whitespace-nowrap ml-1">Short</span>
    </label>
</template>