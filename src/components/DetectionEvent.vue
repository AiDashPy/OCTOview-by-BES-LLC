<script setup>
    defineProps(['date','time','eventType','screenshot','device','unit'])
</script>

<template>
    <div class="shrink-0 my-1 mx-0 p-1 rounded">
        <!-- <img class="h-20 w-auto m-auto rounded hover:blur-sm" src="../assets/img/thumb.jpg" alt="cat locking in"> -->
        <slot />
        <p class="text-xs">{{ date }} - {{  time }}<br>{{ unit }} - {{ device }}<br>{{ eventType }}</p>
    </div>
</template>