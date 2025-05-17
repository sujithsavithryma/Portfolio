<template>
    <Transition name="fade">
        <slot />
    </Transition>
</template>

<script setup>
    import { Transition } from 'vue'
</script>