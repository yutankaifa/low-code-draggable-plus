# low-code-draggable-plus

This package is based on vue draggable plus. For more information, please visit [vue-draggable-plus](https://www.npmjs.com/package/vue-draggable-plus)

## new feature
`modifyDataBeforeAdd`
This property is used for multiple lists. When dragging a list into multiple nested Vue Draggable components, different components may accept different data formats. This property allows the dragged item to be placed before a specific nested component, enabling data processing.

```vue
<template>
  <VueDraggable v-model="list" group="people">
    <div
      v-for="item in list1"
      :key="item.id"
      class="cursor-move h-30 bg-gray-500/5 rounded p-3"
    >
      {{ item.name }}
    </div>
  </VueDraggable>
  <VueDraggable
    v-model="list2"
    group="people"
    :modifyDataBeforeAdd="modifyDataBeforeAdd"
  >
    <div
      v-for="item in list2"
      :key="item.id"
      class="cursor-move h-30 bg-gray-500/5 rounded p-3"
    >
      {{ item.name }}
    </div>
  </VueDraggable>
</template>
<script setup lang="ts">
import { VueDraggable } from "low-code-draggable-plus";
const list1 = ref([
  {
    name: 'Joao',
    id: '1'
  },
  {
    name: 'Jean',
    id: '2'
  },
  {
    name: 'Johanna',
    id: '3'
  },
  {
    name: 'Juan',
    id: '4'
  }
])
const list2 = ref(
  list1.value.map(item => ({
    name: `${item.name}-2`,
    id: `${item.id}-2`
  }))
)
function modifyDataBeforeAdd(data) {
  return {
    ...data,
    name: 'cs'
  }
}
</script>
```
