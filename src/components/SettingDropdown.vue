<script setup>
    defineProps(["name", "selections"])
</script>

<template>
    <div class="mb-4 mr-8 w-fit">
        <p class="mb-1 mr-2  text-sm">{{ name }}</p>
        <select class="bg-zinc-700 rounded p-1" name="encoding" id="encodingDrop">
            <option v-for="selection in selections">{{ selection }}</option>
        </select>
    </div>
</template>