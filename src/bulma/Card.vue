<template>
    <div class="card"
        v-if="!cardState.removed">
        <slot/>
        <loader v-if="loading"/>
    </div>
</template>

<script setup>
import { provide, reactive, watch } from 'vue';
import Loader from '@enso-ui/loader/bulma';

defineOptions({ name: 'Card' });

const props = defineProps({
    collapsed: {
        type: Boolean,
        default: false,
    },
    collapsible: {
        type: Boolean,
        default: false,
    },
    loading: {
        type: Boolean,
        default: false,
    },
});

const emit = defineEmits(['collapse', 'expand', 'remove']);

const cardState = reactive({
    collapsed: props.collapsed,
    collapsible: props.collapsible,
    removed: false,
});

const toggle = () => {
    if (cardState.collapsible) {
        cardState.collapsed = !cardState.collapsed;
        emit(cardState.collapsed ? 'collapse' : 'expand');
    }
};

provide('cardState', cardState);
provide('toggle', toggle);

watch(() => props.collapsed, collapsed => {
    cardState.collapsed = collapsed;
    emit(collapsed ? 'collapse' : 'expand');
});

watch(() => props.collapsible, collapsible => (cardState.collapsible = collapsible));

watch(() => cardState.removed, removed => removed && emit('remove'));
</script>

<style lang="scss">
    .card {
        overflow: hidden;

        &.is-rounded {
            border-radius: 0.5em;
        }

        > .card-header {
            border-bottom: 1px solid var(--enso-surface-border);
        }
    }
</style>
