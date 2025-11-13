<template>
    <header class="card-header"
        :class="[{ 'collapsed': cardState.collapsed }, { 'is-clickable': cardState.collapsible}]">
        <p class="card-header-title is-flex"
            @click="toggle">
            <slot name="title"/>
        </p>
        <div class="is-flex is-flex-shrink-3 min-w-0 overflow-scroll no-scrollbars">
            <slot name="controls"/>
        </div>
        <card-collapse v-if="collapsible"/>
    </header>
</template>

<script setup>
import { inject, defineProps } from 'vue';
import CardCollapse from '../controls/CardCollapse.vue';

defineProps({
    collapsible: {
        type: Boolean,
        default: false,
    },
});

const cardState = inject('cardState');
const toggle = inject('toggle');
</script>

<style lang="scss">
    .card-header {
        border-top-left-radius: inherit;
        border-top-right-radius: inherit;

        &.collapsed {
            border-bottom-left-radius: inherit;
            border-bottom-right-radius: inherit;
        }

        .card-header-title {
            padding: 0.75rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
    }
</style>
