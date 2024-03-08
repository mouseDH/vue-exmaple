<script setup>
import { Panel, useVueFlow } from '@vue-flow/core'
import { v4 as uuidv3 } from 'uuid';

const flowKey = 'example-flow'

const { nodes, addNodes, dimensions, toObject, fromObject } = useVueFlow()

function onSave() {
  console.log(JSON.stringify(toObject()))
  localStorage.setItem(flowKey, JSON.stringify(toObject()))
}

function onRestore() {
  const flow = JSON.parse(localStorage.getItem(flowKey))

  if (flow) {
    fromObject(flow)
  }
}

function onAdd() {

  const newNode = {
    id: uuidv3(),
    label: `Node`,
    position: { x: Math.random() * dimensions.value.width, y: Math.random() * dimensions.value.height },
  }

  addNodes([newNode])
}
</script>

<template>
  <Panel position="top-right" class="save-restore-controls">
    <button style="background-color: #33a6b8" @click="onSave">save</button>
    <button style="background-color: #113285" @click="onRestore">restore</button>
    <!-- <button style="background-color: #6f3381" @click="onAdd">add node</button> -->
  </Panel>
</template>
