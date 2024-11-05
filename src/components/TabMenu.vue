<script setup>
    import SettingsTab from './SettingsTab.vue';
    import SettingDropdown from './SettingDropdown.vue';

    defineProps({
        tabsList: Array
    })

</script>

<template>

    <div class="py-1 rounded-t flex flex-row h-fit">

        <ol class="min-h-full -mt-1 py-0.5">
             <slot />
        </ol>

    </div>

</template>