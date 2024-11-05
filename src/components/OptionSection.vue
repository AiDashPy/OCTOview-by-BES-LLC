<script setup>
    import OptionDrop from './OptionDrop.vue';

    defineProps({
        sectionName: String,
        optionList: Array
    })
</script>

<template>
    <div>
        <h1>{{ sectionName }}</h1>
        <ol>
            <OptionDrop v-for="option in optionList" :optionName="option.optionName" :optionSelects="option.optionSelects" />
        </ol>
    </div>

</template>