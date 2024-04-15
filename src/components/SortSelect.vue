<template>
  <v-select
    label="Сортировать по"
    v-model="selectedSortOrder"
    :items="sortOptions"
    item-title="text"
    item-value="id"
    variant="solo-filled"
    :disabled="props.disabled"
    @update:modelValue="emitSortOrder"
  ></v-select>
</template>

<script setup>
import { ref } from 'vue';

const emit = defineEmits({
  sortOrderChanged: null
});

const props = defineProps({
  disabled: Boolean
});

const sortOptions = [
  {
    text: 'Убыванию рейтинга',
    id: 1
  },
  {
    text: 'Возрастанию рейтинга',
    id: 2
  },
  {
    text: 'По умолчанию',
    id: 3
  }
];
const selectedSortOrder = ref(sortOptions.find(option => option.id === 3));

function emitSortOrder() {
  emit('sortOrderChanged', selectedSortOrder.value)
}
</script>

<style scoped lang="scss">
.select__sort {
  color: #ffffff;
}
</style>