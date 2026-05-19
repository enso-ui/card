<template>
    <card-control>
        <span :class="['tag', type]">
            {{ label }}
        </span>
    </card-control>
</template>

<script setup>
import CardControl from './CardControl.vue';

defineOptions({ name: 'CardBadge' });

defineProps({
    label: {
        type: [String, Number],
        required: true,
    },
    type: {
        type: String,
        default: null,
    },
});
</script>
