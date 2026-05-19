<template>
    <card-control @click="toggle">
        <dropdown-indicator :open="!cardState.collapsed"/>
    </card-control>
</template>

<script setup>
import { inject } from 'vue';
import DropdownIndicator from '@enso-ui/dropdown-indicator';
import CardControl from './CardControl.vue';

defineOptions({ name: 'CardCollapse' });

const cardState = inject('cardState');
const toggle = inject('toggle');
</script>
