<script setup>
import FileReader from "@/components/FileReader.vue";
import RegexInput from "@/components/RegexInput.vue";
import TableViewer from "@/components/TableViewer.vue";
import { ref } from "vue";
</script>

<template>
  <main>
    <FileReader />
    <RegexInput />
    <TableViewer />
  </main>
</template>
