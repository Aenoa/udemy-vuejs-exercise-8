<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="srv !== null">
            <button @click="setNormal">Set to NORMAL</button><br />
            <button @click="setCritical">Set to CRITICAL</button><br />
            <button @click="setUnknown">Set to UNKNOWN</button><br />
        </p>
        <p v-else>Please select a server</p>
    </div>

</template>

<script>
import {EventBus} from '../../main.js'
export default {
    data: function() {
        return {
            srv: null,
        }
    },
    methods: {
        setNormal() {
            this.srv.status = 'normal';
            EventBus.$emit('serverStatusChange', this.srv);
        },
        setCritical() {
            this.srv.status = 'critical';
            EventBus.$emit('serverStatusChange', this.srv);
        },
        setUnknown() {
            this.srv.status = 'unknown';
            EventBus.$emit('serverStatusChange', this.srv);
        }
    },
    created() {
        EventBus.$on('selectedServer', (val) => {
            this.srv = val;
        });
    }
}
</script>

<style>

</style>
