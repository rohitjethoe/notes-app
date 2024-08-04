<script setup>
import { ref } from 'vue';

import Search from '@/components/Search.vue';
import Create from '@/components/Create.vue';
import File from '@/components/File.vue';
import List from '@/components/List.vue';

let query = ref("");
let activeNote = ref(null);

let notes = ref([
  {
    id: 0,
    title: "Hello, World! 🌎",
    post: "This is a Vue 3 tutorial",
    date: new Date().getTime()
  },
  {
    id: 1,
    title: "Hello, Vue!",
    post: "Welcome to a Vue 3 tutorial",
    date: new Date().getTime()
  }
]);

const search = (note) => {
  query.value = note;
}

const view = (note) => {
  activeNote.value = note;
  query.value = "";
}

const create = () => {
  const newNote = {
    id: notes.value.length,
    title: "",
    post: "",
    date: new Date().getTime()
  }

  notes.value.push(newNote);
  activeNote.value = newNote;
}

const edit = (note) => {
  notes.value[activeNote.value.id].title = note.newTitle;
  notes.value[activeNote.value.id].post = note.newPost;
}
</script>

<template>
  <Search @update:modelValue="search($event)" @close-note="view" :modelValue="query" :listView="activeNote === null" />
  <main>
    <List v-if="activeNote === null" @open-note="view" :notes :modelValue="query"/>
    <File v-if="activeNote !== null" @edit-note="edit($event)" :title="activeNote.title" :post="activeNote.post"/>
  </main>
  <Create @create-note="create()" :notes="notes.length" />
</template>

