<template>
    <div class="card p-2">
        <div class="input-group">
            <input type="text" class="form-control" :value="value" v-on="listeners" placeholder="Type a name">
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            value: {
                type: String,
                default: '',
            }
        },
        computed: {
            listeners() {
                return {
                    // Pass all component listeners directly to input
                    ...this.$listeners,
                    // Override input listener to work with v-model
                    input: event => this.$emit('input', event.target.value)
                }
            }
        }
    }
</script>

<style scoped>
    .input {
        width: 100%;
        padding: 8px 10px;
        border: 1px solid #32485F;
    }
</style>
