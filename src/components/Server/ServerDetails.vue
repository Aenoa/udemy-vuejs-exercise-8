<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="srv !== null">
            <button>Set to NORMAL</button><br />
            <button>Set to CRITICAL</button><br />
            <button>Set to UNKNOWN</button><br />
        </p>
        <p v-else>Please select a server</p>
    </div>

</template>

<script>
export default {
    props: {
        srv: {
            type: Object,
            default: null,
        }
    },
    methods: {
        setNormal() {
            this.srv.status = 'normal';
        },
        setCritical() {
            this.srv.status = 'critical';
        },
        setUnknown() {
            this.srv.status = 'unknown';
        }
    }
}
</script>

<style>

</style>
