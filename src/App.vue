<script setup>
import { ref } from 'vue';

import Search from '@/components/Search.vue';
import Create from '@/components/Create.vue';
import File from '@/components/File.vue';
import List from '@/components/List.vue';

const activeNote = ref(0);
const notes = ref([
  {
    title: "Hello, World! 🌎",
    post: "This is a Vue 3 tutorial",
    date: new Date().getTime()
  },
  {
    title: "Hello, World! 🌎",
    post: "This is a Vue 3 tutorial",
    date: new Date().getTime()
  }
]);
</script>

<template>
  <Search />
  <main>
    <List :notes />
    <!-- <File :title="notes[activeNote].title" :post="notes[activeNote].post"/> -->
  </main>
  <Create :notes="notes.length" />
</template>

