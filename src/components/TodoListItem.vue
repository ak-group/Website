<template>
    <li class="list-group-item d-flex justify-content-between lh-condensed">
        <div>
            <h6 class="my-0">{{ todo.text }}</h6>
            <small class="text-muted">Brief description</small>
        </div>
        <span class="text-muted">${{Number(Math.random() * 10).toFixed(0)}}</span>
        <span class="text-muted">
            <button @click="$emit('remove', todo.id)">X</button>
        </span>
    </li>
</template>

<script>
    export default {
        props: {
            todo: {
                type: Object,
                required: true
            }
        }
    }
</script>