<template>
    <enso-form class="box form-box has-background-light raises-on-hover"
        ref="form"
        @loaded="ready = true">
        <template v-slot:suppliers="{ sectionBindings }">
            <div class="column">
                <div class="columns">
                    <div class="column is-6-tablet">
                        <form-field :field="$refs.form.field('suppliers')"
                            @input="prefill"
                            ref="suppliers"/>
                    </div>
                    <div class="column is-6-tablet">
                        <form-field :field="$refs.form.field('defaultSupplierId')"
                            :params="selectedSuppliers"
                            ref="suppliers"/>
                    </div>
                </div>
                <supplier-details
                    v-on="$listeners"
                    :supplier="supplier"
                    :key="supplier.id"
                    v-for="supplier in suppliers"/>
            </div>
        </template>
    </enso-form>
</template>

<script>
import { EnsoForm, FormField } from '@enso-ui/bulma';
import SupplierDetails from './SupplierDetails';
export default {
    name: 'BaseForm',

    components: { EnsoForm, FormField, SupplierDetails },

    inject: ['i18n'],

    data: () => ({
        ready: false,
    }),

    computed: {
        suppliers() {
            return this.ready ? this.$refs.form.field('suppliers').value : [];
        },
        selectedSuppliers() {
            return {
                id: this.suppliers.map(({ id }) => id),
            };
        },
        productPartNumber() {
            return this.ready && this.$refs.form.field('part_number').value;
        }
    },

    methods: {
        prefill() {
            this.suppliers
                .filter(({pivot}) => !pivot.part_number)
                .forEach(({pivot}) => pivot.part_number = this.productPartNumber);
        }
    }
};
</script>

<style scoped>

</style>
