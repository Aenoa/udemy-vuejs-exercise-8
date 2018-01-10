<template>
    <li class="list-group-item" @click="onSelected(me)">Server #{{ me.id }} &bull; status: {{me.status}}</li>
</template>

<script>
export default {
    props: {
        me: {
            type: Object,
            required: true,
        },
        onSelected: {
            type: Function,
            required: true,
        }
    },
}
</script>