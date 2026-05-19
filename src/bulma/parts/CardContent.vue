<template>
    <collapse :show="!cardState.collapsed"
        v-if="cardState.collapsible">
        <div class="card-content"
            v-bind="$attrs">
            <slot/>
        </div>
    </collapse>
    <div class="card-content"
        v-bind="$attrs"
        v-else>
        <slot/>
    </div>
</template>

<script setup>
import { inject } from 'vue';
import { Collapse } from '@enso-ui/transitions';

defineOptions({
    name: 'CardContent',
    inheritAttrs: false,
});

const cardState = inject('cardState');
</script>
