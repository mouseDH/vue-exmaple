<script setup>
import { ref } from 'vue'
import { VueFlow, useVueFlow } from '@vue-flow/core'
import DropzoneBackground from './components/DropzoneBackground.vue'
import Sidebar from './components/Sidebar.vue'
import useDragAndDrop from './components/useDnD'
import SaveRestoreControls from './components/Controls.vue'
import InteractionControls from './components/InteractionControls.vue'

const { onConnect, addEdges } = useVueFlow()

const { onDragOver, onDrop, onDragLeave, isDragOver } = useDragAndDrop()

const nodes = ref([])

const edges = ref([])

function handleEdgeClick(event){
    console.log(JSON.stringify(event))
}

function handleEdgeDoubleClick(event){
  console.log(JSON.stringify(event))
  console.log(JSON.stringify(event.edge))
}

</script>

<template>
    <div class="dndflow" @drop="onDrop">
    <VueFlow :nodes="nodes" @dragover="onDragOver" @dragleave="onDragLeave" :edges="edges" 
    class="interactionflow"  @edgeClick="handleEdgeClick" @edgeDoubleClick="handleEdgeDoubleClick" fit-view-on-init>
      <SaveRestoreControls />
      
      <DropzoneBackground
        :style="{
          backgroundColor: isDragOver ? '#e7f3ff' : 'transparent',
          transition: 'background-color 0.2s ease',
        }"
      />
      <InteractionControls />
    </VueFlow>

    <Sidebar />
  </div>
</template>
