<script setup>
import { ref } from 'vue';

import Search from '@/components/Search.vue';
import Create from '@/components/Create.vue';
import File from '@/components/File.vue';
import List from '@/components/List.vue';

let activeNote = ref(null);
const notes = ref([
  {
    id: 0,
    title: "Hello, World! 🌎",
    post: "This is a Vue 3 tutorial",
    date: new Date().getTime()
  },
  {
    id: 1,
    title: "Hello, World! 🌎",
    post: "This is a Vue 3 tutorial",
    date: new Date().getTime()
  }
]);

const noteHandler = (note) => {
  activeNote.value = note;
}
</script>

<template>
  <Search @close-note="noteHandler" :listView="activeNote === null" />
  <main>
    <List v-if="activeNote === null" @open-note="noteHandler" :notes />
    <File v-if="activeNote !== null" :title="activeNote.title" :post="activeNote.post"/>
  </main>
  <Create :notes="notes.length" />
</template>

