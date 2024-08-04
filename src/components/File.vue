<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['edit-note']);

defineProps({
    title: String,
    post: String
})

const editNote = () => {
    const newTitle = document.querySelector('.notes-file__title--input').value;
    const newPost = document.querySelector('.notes-file__post--input').value;
    emit('edit-note', { newTitle, newPost });
}

</script>

<template>
    <section class="notes-file">
        <div class="notes-file__title">
            <input class="notes-file__title--input" @input="editNote" :value="title" type="text" name="" id="">
        </div>
        <div class="notes-file__post">
            <textarea class="notes-file__post--input" @input="editNote" :value="post"></textarea>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.notes-file {
    &__title {
        width: calc(100vw - 2.5rem);
        margin: 0.75rem auto 0;
        caret-color: #E4AF0A;
        input {
            font-family: 'SF Pro', sans-serif;
            font-size: 2rem;
            background-color: #f2f2f7;
            border: none;
            outline: none;
            width: 100%;
            font-weight: 700;
            letter-spacing: -0.027rem;
        }
    }
    &__post {
        width: calc(100vw - 2.5rem);
        margin: 0.75rem auto;
        caret-color: #E4AF0A;
        textarea {
            font-family: 'SF Pro', sans-serif;
            font-size: 1.125rem;
            background-color: #f2f2f7;
            height: 66vh;
            color: #454545;
            border: none;
            outline: none;
            width: 100%;
            font-weight: 400;
            letter-spacing: -0.027rem;
            resize: none;
        }
    }
}
</style>