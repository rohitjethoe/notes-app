<script setup>
import { ref } from 'vue';

const query = ref("");
</script>

<template>
    <header class="notes-header">
        <div class="notes-header__wrapper">
            <input class="notes-header__input" type="text" placeholder="Search" v-model="query">
        </div>
    </header>
</template>