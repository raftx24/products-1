<template>
    <div class="columns is-centered">
        <div class="column is-three-quarters-desktop is-full-touch">
            <base-form/>
        </div>
    </div>
</template>

<script>
import BaseForm from './components/BaseForm';

export default {
    name: 'Create',

    components: { BaseForm },
};
</script>
