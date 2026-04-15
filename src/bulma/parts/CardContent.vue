<template>
    <collapse class="card-content"
        :show="!cardState.collapsed"
        v-if="cardState.collapsible">
        <slot/>
    </collapse>
    <div class="card-content"
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
};
</script>
