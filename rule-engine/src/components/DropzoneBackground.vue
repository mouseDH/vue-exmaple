<!-- 画布背景 -->
<script lang="ts" setup>
import { Background } from '@vue-flow/background'
</script>

<template>
  <div style="height: 100%; width: 100%">
    <Background :size="2" :gap="20" pattern-color="#BDBDBD" variant="lines">
      <slot />
    </Background>
  </div>
</template>
