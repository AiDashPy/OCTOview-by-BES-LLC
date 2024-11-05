<script setup>
    import TabMenu from './TabMenu.vue';
    import TabDisplay from './TabDisplay.vue';

    defineProps(['tabsList', 'settings'])
</script>

<template>
    <div class="h-1/4 px-8 pt-5 pb-0 text-white bg-zinc-800 rounded m-1 mt-2">

        <TabMenu :tabsList="tabsList" />
        <TabDisplay :settings="settings" />

    </div>

</template>