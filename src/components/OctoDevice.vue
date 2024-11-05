<script setup>
    defineProps(['name'])
</script>

<template>
    <a><li class="inline pb-2 px-2 pt-1 align-middle rounded-t-xl max-sm:rounded-b-xl hover:bg-zinc-700" href="#">{{ name }}</li></a>
</template>