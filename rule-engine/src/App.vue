<script setup>
import { ref } from 'vue'
import { VueFlow, useVueFlow } from '@vue-flow/core'
import DropzoneBackground from './components/DropzoneBackground.vue'
import Sidebar from './components/Sidebar.vue'
import useDragAndDrop from './components/useDnD'
import SaveRestoreControls from './components/Controls.vue'
import InteractionControls from './components/InteractionControls.vue'

const { addEdges, updateEdge } = useVueFlow()

const { onDragOver, onDrop, onDragLeave, isDragOver } = useDragAndDrop()

const nodes = ref([])

const edges = ref([])

</script>

<template>
  <div class="dndflow" @drop="onDrop">
    <Sidebar />
    <VueFlow :nodes="nodes" :edges="edges" class="interactionflow" @dragover="onDragOver" @dragleave="onDragLeave"
     
      fit-view-on-init>
      <SaveRestoreControls />

      <DropzoneBackground :style="{
    backgroundColor: isDragOver ? '#e7f3ff' : 'transparent',
    transition: 'background-color 0.2s ease',
  }" />
      <InteractionControls />
    </VueFlow>

    
  </div>
</template>
