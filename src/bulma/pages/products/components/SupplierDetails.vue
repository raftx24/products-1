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
                    v-focus
                    v-select-on-focus
                    @input="$emit('part-number-updated')"
                    v-model="supplier.pivot.part_number">
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
                    v-select-on-focus
                    @input="$emit('acquisition-price-updated')"
                    v-model="supplier.pivot.acquisition_price">
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
    name: 'SupplierDetails',
    props: {
        supplier: {
            type: Object,
            required: true,
        }
    },

    inject: ['i18n'],

    directives: { focus, selectOnFocus }
};
</script>
