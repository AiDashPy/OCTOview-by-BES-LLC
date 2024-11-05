<script setup>
    defineProps({
        alert: String
    })
</script>

<template>
    <header class="py-1 mb-1 w-screen border-b border-zinc-900 md:px-56">
        <div class="flex flex-row mx-2">
        <div class="w-1/3">
            <img class="h-14 rounded border border-zinc-900" src="../assets/img/BESLogo.webp" alt="Bailey's Electrical Services, LLC Logo">
        </div>
        <div class="w-1/3 self-center">
            <h1 class="text-center text-red-600 font-bold md:text-xl"><a href="#">⯃ {{ alert }}</a></h1>
        </div>
        <div class="w-1/3">
            <img class="ml-auto h-14 -mx-5" src="../assets/img/octa.png" alt="Bailey's Electrical Services, LLC Logo">
        </div>
        </div>
    </header>
</template>