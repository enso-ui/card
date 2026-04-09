<template>
    <card-control @click="$emit('refresh')">
        <span class="icon is-small">
            <fa :icon="faSync"/>
        </span>
    </card-control>
</template>

<script>
import { FontAwesomeIcon as Fa } from '@fortawesome/vue-fontawesome';
import { faSync }
from '@fortawesome/free-solid-svg-icons';
import CardControl from './CardControl.vue';

export default {
    name: 'CardRefresh',

    components: { Fa, CardControl },

    data: () => ({
        faSync,
    }),

    emits: ['refresh'],
};

</script>
