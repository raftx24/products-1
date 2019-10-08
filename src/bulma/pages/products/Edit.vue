<template>
    <div class="columns is-centered">
        <div class="column is-three-quarters-desktop is-full-touch">
            <base-form/>
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
import { Accessories, Tab, Documents, Comments } from '@enso-ui/bulma';
import BaseForm from './components/BaseForm';

export default {
    name: 'Edit',

    components: { BaseForm, Accessories, Tab, Documents, Comments },

    inject: ['i18n'],

    data: () => ({
        ready: false,
    }),

    computed: {
        id() {
            return Number.parseInt(this.$route.params.product, 10);
        },
    },
};
</script>
