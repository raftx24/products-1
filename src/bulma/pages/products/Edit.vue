<template>
    <div class="columns is-centered">
        <div class="column is-three-quarters-desktop is-full-touch">
            <enso-form class="box form-box has-background-light raises-on-hover"
                ref="form"
                @loaded="selectedSuppliers.id = $refs.form.field('suppliers').value;">
                <template v-slot:suppliers="{ field }">
                    <form-field :field="field"
                        @input="selectedSuppliers.id = $event"
                        ref="suppliers"/>
                </template>
                <template v-slot:defaultSupplierId="{ field }">
                    <form-field :field="field"
                        :params="selectedSuppliers"
                        ref="defaultSupplier"/>
                </template>
            </enso-form>
            <accessories>
                <template slot-scope="{ count }">
                    <tab keep-alive
                         id="Comments">
                        <div class="columns is-centered">
                            <div class="column is-two-thirds">
                                <comments :id="id"
                                    type="product"
                                    @update="$set(count, 'Comments', $refs.comments.count)"
                                    ref="comments"/>
                            </div>
                        </div>
                    </tab>
                    <tab keep-alive
                         id="Documents">
                        <div class="columns is-centered">
                            <div class="column is-two-thirds">
                                <documents :id="id"
                                    type="product"
                                    @update="$set(count, 'Documents', $refs.documents.count)"
                                    ref="documents"/>
                            </div>
                        </div>
                    </tab>
                </template>
            </accessories>
        </div>
    </div>
</template>

<script>
import { EnsoForm, FormField, Accessories, Tab, Documents, Comments } from '@enso-ui/bulma';

export default {
    name: 'Edit',

    components: { EnsoForm, FormField, Accessories, Tab, Documents, Comments },

    data: () => ({
        selectedSuppliers: { id: [] },
    }),

    computed: {
        id() {
            return Number.parseInt(this.$route.params.product, 10);
        },
    },
};
</script>

<style lang="scss">
</style>
