<template>
  <li class="node-tree">

    <ul v-if="node.childs && node.childs.length">
      <node v-for="child in node.childs" :node="child"></node>
    </ul>
  </li>
</template>

<script setup lang="ts">
 

 defineProps({
 	node:{
 		type: Object
 	}
 })
</script>