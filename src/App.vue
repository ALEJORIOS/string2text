<script setup lang="ts">
import { ref } from "vue";
let input:string = "";
const result = ref<null | HTMLPreElement>(null);

function updateInput(rawInput: string) {
  input = rawInput;
}

function translate() {
  const output: string = input.replaceAll('\n',"eyyyyyyyy")
  console.log(">> ", output)
  result.value!.innerHTML = output;
}
</script>

<template>
  <div class="container">
    <textarea @input="updateInput(($event.target as HTMLTextAreaElement)?.value)"></textarea>
    <pre ref="result" style="white-space: pre-line;"></pre>
    <div class="actions">
      <button @click="translate">Convertir</button>
    </div>
  </div>
</template>

<style>
.container {
  display: grid;
  box-sizing: border-box;
  grid-template-columns: repeat(2, 1fr) auto;
  width: 100vw;
  height: 100vh;
  gap: 2rem;
  padding: 1rem;
}
</style>
