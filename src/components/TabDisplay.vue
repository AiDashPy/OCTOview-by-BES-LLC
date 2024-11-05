<script setup>
    import TabMenu from './TabMenu.vue';
    import SettingDropdown from './SettingDropdown.vue';
    // import deviceSetting from './deviceSetting.vue';

    defineProps(['settings'])
</script>

<template>

    <div class="flex flex-col shrink flex-wrap pb-5 content-start pt-2 mt-1 pl-4">

        <slot />

    </div>

</template>