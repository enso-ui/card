<template>
    <card-control @click="refresh">
        <span class="icon is-small">
            <fa :icon="faSync"
                :spin="loading"/>
        </span>
    </card-control>
</template>

<script setup>
import { FontAwesomeIcon as Fa } from '@fortawesome/vue-fontawesome';
import { faSync }
from '@fortawesome/free-solid-svg-icons';
import CardControl from './CardControl.vue';

defineOptions({ name: 'CardRefresh' });

const props = defineProps({
    loading: {
        type: Boolean,
        default: false,
    },
});

const emit = defineEmits(['refresh']);

const refresh = () => !props.loading && emit('refresh');
</script>
