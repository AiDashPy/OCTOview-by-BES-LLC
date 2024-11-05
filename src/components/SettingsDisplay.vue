<script setup>
    import SettingDropdown from './SettingDropdown.vue';

    defineProps({
        name: String,
    })
</script>

<template>
    <div class="h-full pb-8 rounded-b bg-zinc-800">
        <div class="flex flex-col flex-wrap h-full mt-2 mx-6">
            <slot />
        </div>
    </div>
</template>