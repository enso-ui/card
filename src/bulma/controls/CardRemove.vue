<template>
    <card-control @click="cardState.removed = true">
        <a class="delete is-small"/>
    </card-control>
</template>

<script setup>
import { inject } from 'vue';
import CardControl from './CardControl.vue';

defineOptions({ name: 'CardRemove' });

const cardState = inject('cardState');
</script>
