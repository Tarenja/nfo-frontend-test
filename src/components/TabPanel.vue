<script setup>

    import { inject } from 'vue';

    const props = defineProps(['id'])

    const activeTab = inject("activeTab")
    const activeSubTab = inject("activeSubTab")

</script>

<template>
    <div class="tab-panel" v-show="id == activeTab || id == activeSubTab">
        <slot></slot>
    </div>
</template>


<style scoped>
    .tab-panel {
        background-color: light-dark(var(--light-panel), var(--dark-panel));
        margin-top: 8px;
        max-width: 100%;
        padding: 16px;
        border-radius: 8px;
    }
</style>
