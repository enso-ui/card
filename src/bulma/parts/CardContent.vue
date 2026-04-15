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

<script>
import { Collapse } from '@enso-ui/transitions';

export default {
    name: 'CardContent',

    components: { Collapse },

    inject: ['cardState'],

    inheritAttrs: false,
};
</script>
