<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <server v-for="srv in servers" :key="srv.id" :onSelected="select" :me="srv"></server>
        </ul>
    </div>
</template>

<script>
import Server from './Server.vue'
import {EventBus} from '../../main'
export default {
    components: {
        server: Server,
    },
    data: function() {
        return {
            selected: null,
            servers: [
                {
                    id: 1, status: 'normal',
                },
                {
                    id: 2, status: 'critical',
                },
                {
                    id: 3, status: 'unknown',
                },
                {
                    id: 4, status: 'normal',
                }
            ]
        }
    },
    methods: {
        select(val) {
            console.log('selected',val);
            this.selected = val;
        }
    },
    created() {
        EventBus.$on('editedServer', (value) => {
            console.log('the following server was edited', value);
        });
    }
}
</script>

<style>

</style>
