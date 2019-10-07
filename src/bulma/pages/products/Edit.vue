<template>
    <div class="columns is-centered">
        <div class="column is-three-quarters-desktop is-full-touch">
            <enso-form class="box form-box has-background-light raises-on-hover"
                ref="form"
                @loaded="selectedSuppliers.id = $refs.form.field('suppliers').value; ready = true">
                <template v-slot:suppliers="{ sectionBindings }">
                    <div class="column">
                        <div class="columns">
                            <div class="column is-6-tablet">
                                <form-field :field="$refs.form.field('suppliers')"
                                            @input="selectedSuppliers.id = $event"
                                            ref="suppliers"/>
                            </div>
                            <div class="column is-6-tablet">
                                <form-field :field="$refs.form.field('defaultSupplierId')"
                                            @input="selectedSuppliers.id = $event"
                                            ref="suppliers"/>
                            </div>
                        </div>
                        <div class="columns"
                             v-for="supplier in suppliers">
                            <p>gigi</p>
                        </div>
                    </div>
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
        ready: false,
        selectedSuppliers: { id: [] },
    }),

    computed: {
        id() {
            return Number.parseInt(this.$route.params.product, 10);
        },
        suppliers() {
            return this.ready && this.$refs.form.field('suppliers').value;
        }
    },
};
</script>

<style lang="scss">
</style>
