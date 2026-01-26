<script setup>
    import { ref, provide } from 'vue';

    const model = defineModel();
    const props = defineProps();
    const slots = defineSlots();

    const tabsContent = ref(slots.default().map((tab) => tab.props))

    const activeTab = model;

    provide("activeTab", activeTab)

</script>

<template>
    <div class="tab-component">
        <ul class="tabs-header">
            <li 
                v-for="tab in tabsContent" 
                :key="tab.id" 
                @click="activeTab = tab.id"
                class="tab-label"
            >
                <span class="material-icons">{{ tab.imageText }}</span>
                {{ tab.label }}
                <span class="tab-suffix">{{ tab.suffix }}</span>
            </li>
        </ul>
        <slot></slot>
    </div>
</template>


<style scoped>
    .tab-component {
        background-color: light-dark(var(--light-bg), var(--dark-bg));
        padding: 46px 48px;
	    color: light-dark(black, white);
        margin-top: 32px;
    }

    .tabs-header {
        list-style: none;
        display: flex;
        align-items: flex-start;
        align-self: center;
        padding: 0;
        margin: 0;
        gap: 8px;
        .tab-label {
            padding: 12px 16px;
            border: 1px solid light-dark(var(--light-border), var(--dark-border));
            height: 43px;
            display: flex;
            align-items: center;
            font-weight: 400;
            font-size: 19px;
        }
        .material-icons {
            margin-right: 8px;
        }
        .tab-suffix {
            margin-left: 8px;
        }

    }
</style>
