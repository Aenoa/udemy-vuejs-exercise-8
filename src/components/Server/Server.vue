<template>
    <li class="list-group-item" @click="onSelected(me)">Server #{{ me.id }} &bull; status: {{me.status}}</li>
</template>

<script>
import {EventBus} from '../../main.js'
export default {
    props: {
        me: {
            type: Object,
            required: true,
        }
    },
    methods: {
        onSelected(elem) {
            console.log('emitting from Server.vue');
            EventBus.$emit('selectedServer', this.me);
        }
    },
    created() {
        EventBus.$on('serverStatusChange', (val) => {
            console.log('event received')
            if(val.id === this.me.id) {
                this.me.status = val.status;
            }
        });
    }
}
</script>