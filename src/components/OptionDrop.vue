<script setup>
    defineProps({
        optionName: String,
        optionSelects: Array,
    })
</script>

<template>
    <h1 class="bg-white w-fit">{{ optionName }}</h1>
    <select class="bg-white">
        <option v-for="select in optionSelects">{{ select }}</option>
    </select>
</template>