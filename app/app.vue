<script setup>
const items = ref([
  {
    label: 'Backlog',
    icon: 'i-lucide-circle-help'
  },
  {
    label: 'Todo',
    icon: 'i-lucide-circle-plus'
  },
  {
    label: 'In Progress',
    icon: 'i-lucide-circle-arrow-up'
  },
  {
    label: 'Done',
    icon: 'i-lucide-circle-check'
  }
])
const value = ref({
  label: 'Backlog',
  icon: 'i-lucide-circle-help'
})

const searchTerm = ref('');

const searchTermEvents = ref([]);

function onUpdateSearchTerm(_searchTerm) {
  console.log('onUpdateSearchTerm', _searchTerm)
  searchTermEvents.value.push({
    timestamp: Date.now(),
    searchTerm: _searchTerm
  })
}
</script>

<template>
  <div class="flex gap-4 p-8">
    <USelectMenu
      v-model="value"
      v-model:search-term="searchTerm"
      :search-input="{
        placeholder: 'Filter...',
        icon: 'i-lucide-search'
      }"
      :items="items"
      class="w-48 max-h-8"
      @update:search-term="onUpdateSearchTerm"
    />
    <div>
      <div class="font-bold">Searchterm event updates</div>
      <ul>
        <li v-for="ev in searchTermEvents" :key="ev">
          {{ ev }}
        </li>
      </ul>
    </div>
  </div>
</template>
