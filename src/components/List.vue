<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
    notes: Array,
    modelValue: String
});

const weekDays = ['Sunday','Monday','Tuesday','Wednesday','Thursday','Friday','Saturday'];

const isSameDay = (timestamp) => {
    const date = new Date(timestamp);
    const today = new Date();

    return date.getFullYear() === today.getFullYear() 
        && date.getMonth() === today.getMonth() 
        && date.getDate() === today.getDate();
}

</script>

<template>
    <section class="notes-list">
        <div class="notes-list__wrapper">
            <div @click="$emit('open-note', note)" v-for="(note, i) in notes" class="notes-list__note" :class="i == notes.length - 1 ? 'notes-list__note--last' : ''">
                <div class="notes-list__crate" v-if="note.title.includes(modelValue)">
                    <div class="notes-list__title">
                        {{ note.title }}
                    </div>
                    <div class="notes-list__description">
                        <span v-if="isSameDay(note.date)">{{ new Date(note.date).getHours() < 12 ?  `0${new Date(note.date).getHours()}` : new Date(note.date).getHours() }}:{{ new Date(note.date).getMinutes() }} {{ note.post }}</span>
                        <span v-else>{{ weekDays[new Date(note.date).getDay()] }} {{ note.post }}</span>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.notes-list {
    $nl: &;

    padding: 1.375rem 0;

    &__wrapper {
        width: calc(100vw - 1.25rem);
        margin: 0 auto;
        border-radius: 0.625rem;
        background-color: #FFF;
    }

    &__title {
        font-family: 'SF Pro', sans-serif;
        font-weight: 700;
        letter-spacing: -0.027rem;
    }

    &__description {
        font-family: 'SF Pro', sans-serif;
        color: #8A8A8E;
        letter-spacing: -0.014rem;
    }

    &__note {
        padding: 0.75rem 1.75rem;
        padding-bottom: 0;
        border-bottom-left-radius: 0;
        border-bottom-right-radius: 0;
        border-top-left-radius: 0.625rem;
        border-top-right-radius: 0.625rem;
        &:hover {
            background-color: rgba(228, 175, 10, 0.4);
            transition: 250ms background-color ease-out;
        }
        &--last {
            border-top-left-radius: 0;
            border-top-right-radius: 0;
            border-bottom-left-radius: 0.625rem;
            border-bottom-right-radius: 0.625rem;
            border-bottom: none;
            #{$nl}__crate {
                border-bottom: none;
            }
        }
    }

    &__crate {
        display: flex;
        flex-direction: column;
        gap: 0.3rem;
        border-bottom: 0.063rem solid #C7C7CC;
        padding-bottom: 0.75rem;
    }
}
</style>