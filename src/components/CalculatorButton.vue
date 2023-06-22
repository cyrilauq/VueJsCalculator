<template>
    <button @click="$emit('click', content)">
        {{ content }}
    </button>
</template>

<script setup lang="ts">
    const props = defineProps({
        content: String
    })

    const emits = defineEmits([
        'click'
    ])
</script>

<style scoped>

</style>