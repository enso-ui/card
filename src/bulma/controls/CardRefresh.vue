<template>
    <card-control @click="refresh">
        <span class="icon is-small">
            <fa :icon="faSync"
                :spin="loading"/>
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

    props: {
        loading: {
            type: Boolean,
            default: false,
        },
    },

    data: () => ({
        faSync,
    }),

    emits: ['refresh'],

    methods: {
        refresh() {
            if (!this.loading) {
                this.$emit('refresh');
            }
        },
    },
};

</script>
