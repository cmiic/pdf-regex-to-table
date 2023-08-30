<script setup>
import { ref } from "vue";
const regex = ref("");
regex.value =
  "/Klasse: ([0-9][a-z])\n.*([A-Z0-9]{4}-[A-Z0-9]{4}-[A-Z0-9]{4})/gm";
</script>
<template>
  <div class="field">
    <label class="label">Regex</label>
    <div class="control">
      <input
        class="input is-family-monospace"
        type="text"
        placeholder="Text input"
        v-model="regex"
      />
    </div>
  </div>
</template>
