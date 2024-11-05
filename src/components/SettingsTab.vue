<script setup>
    import TabDisplay from './TabDisplay.vue';

    defineProps({
        name: String,
        active: {
            type: Boolean,
            default: false,
        },
    })
</script>

<template>
    
    <li v-if="active" class="rounded-t inline px-1 pb-2 pt-1 bg-zinc-800 text-white hover:bg-zinc-700">
        <a class=" select-none" >{{ name }}</a>
    </li>


    <li v-else class="rounded-t inline px-1 pb-2 pt-1 text-white hover:bg-zinc-700">
        <a class=" select-none" >{{ name }}</a>
    </li>



    <!-- <div v-if="active" class="h-full rounded-b rounded-br">
        <div class="bg-red-400 flex flex-col flex-wrap pb-2 content-start pt-2 mt-1 pl-4">

            <slot />

        </div>
    </div>

    <div v-else class="h-full hidden">
        <div class="h-full flex flex-col shrink flex-wrap pb-2 content-start pt-2 mt-1 pl-4">

            <slot />

        </div>
    </div> -->


</template>