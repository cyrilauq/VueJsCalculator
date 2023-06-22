<template>
    <button>
        {{ content }}
    </button>
</template>

<script setup lang="ts">
    const props = defineProps({
        content: String
    })
</script>

<style scoped>

</style>