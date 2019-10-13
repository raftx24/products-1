<template>
    <div class="columns">
        <div class="column is-3">
            <div class="field">
                <label class="label">
                    {{ i18n('Supplier') }}
                </label>
            </div>
            <div class="control">
                <input class="input"
                    :value="supplier.name"
                    readonly>
            </div>
        </div>
        <div class="column is-3">
            <div class="field">
                <label class="label">
                    {{ i18n('Part Number') }}
                </label>
            </div>
            <div class="control">
                <input class="input"
                    v-model="supplier.pivot.part_number"
                    v-focus
                    v-select-on-focus
                    @input="$emit('part-number-updated')">
            </div>
        </div>
        <div class="column is-2">
            <div class="field">
                <label class="label">
                    {{ i18n('Acquisition Price') }}
                </label>
            </div>
            <div class="control">
                <input class="input"
                    v-model="supplier.pivot.acquisition_price"
                    v-select-on-focus
                    @input="$emit('acquisition-price-updated')">
            </div>
        </div>
        <div class="column is-2">
            <div class="field">
                <label class="label">
                    {{ i18n('Mapped At') }}
                </label>
            </div>
            <div class="control">
                <input class="input"
                    :value="supplier.pivot.created_at"
                    readonly>
            </div>
        </div>
        <div class="column is-2">
            <div class="field">
                <label class="label">
                    {{ i18n('Updated At') }}
                </label>
            </div>
            <div class="control">
                <input class="input"
                    :value="supplier.pivot.updated_at"
                    readonly>
            </div>
        </div>
    </div>
</template>

<script>
import { focus, selectOnFocus } from '@enso-ui/directives';

export default {
    name: 'Supplier',

    directives: { focus, selectOnFocus },

    inject: ['i18n'],

    props: {
        supplier: {
            type: Object,
            required: true,
        },
    },
};
</script>
