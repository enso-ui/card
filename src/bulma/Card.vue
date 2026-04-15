<template>
    <div class="card"
        v-if="!cardState.removed">
        <slot/>
        <overlay v-if="overlay"/>
        <loader size="medium"
            v-else-if="loading"/>
    </div>
</template>

<script>
import Loader from '@enso-ui/loader/bulma';
import Overlay from '@enso-ui/loader/bulma/overlay';

export default {
    name: 'Card',

    components: { Loader, Overlay },

    provide() {
        return {
            cardState: this.cardState,
            toggle: this.toggle,
        };
    },

    props: {
        collapsed: {
            type: Boolean,
            default: false,
        },
        collapsible: {
            type: Boolean,
            default: false,
        },
        overlay: {
            type: Boolean,
            default: false,
        },
        loading: {
            type: Boolean,
            default: false,
        },
    },

    emits: ['collapse', 'expand', 'remove'],

    data: v => ({
        cardState: {
            collapsed: v.collapsed,
            collapsible: v.collapsible,
            removed: false,
        },
    }),

    watch: {
        collapsed(collapsed) {
            this.cardState.collapsed = collapsed;
            this.$emit(collapsed ? 'collapse' : 'expand');
        },
        'cardState.removed': 'remove',
    },

    methods: {
        toggle() {
            if (this.cardState.collapsible) {
                this.cardState.collapsed = !this.cardState.collapsed;
                this.$emit(this.cardState.collapsed ? 'collapse' : 'expand');
            }
        },
        remove() {
            this.$emit('remove');
        },
    },
};
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
