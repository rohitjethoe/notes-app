<script setup>
import { defineProps } from 'vue';

defineProps({
    title: String,
    post: String
})
</script>

<template>
    <section class="notes-file">
        {{ title }}
        {{ post }}
    </section>
</template>