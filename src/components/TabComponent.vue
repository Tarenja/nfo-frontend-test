<script setup>
    import { ref, provide } from 'vue';

    const model = defineModel();
    const slots = defineSlots();

    const tabsContent = ref(slots.default().map((tab) => tab.props))

    const activeTab = model;
    const activeSubTab = model;

    provide("activeTab", activeTab)
    provide("activeSubTab", activeSubTab)

    function setActiveTab(tab) {
        if(!tab.disabled) { this.activeTab = tab.id }
    }

</script>

<template>
    <div class="tab-component">
        <ul class="tabs-header">
            <li 
                v-for="tab in tabsContent" 
                :key="tab.id" 
                @click="setActiveTab(tab)"
                class="tab-label"
                :class="{'selected-tab': tab.id == activeTab, disabled: tab.disabled}"
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
        flex-wrap: wrap;
        padding: 0;
        margin: 0;
        gap: 8px;
        width: 100%;
        @media screen and (max-width: 820px){
            flex-direction: column;
            align-content: center;
        }
        .tab-label {
            padding: 12px 16px;
            border: 1px solid light-dark(var(--light-border), var(--dark-border));
            border-radius: 8px;
            display: flex;
            align-items: center;
            font-size: 16px;
            cursor: pointer;
            background-color: light-dark(white, var(--dark-panel));
            &:hover {
                border-color: light-dark(var(--light-border-focus), var(--dark-border-focus))
            }
            &.selected-tab {
                background-color: light-dark(var(--light-accent), var(--dark-accent));
            }
            &.disabled {
                color: light-dark(var(--light-muted), var(--dark-muted));
                cursor: not-allowed;
            }
            @media screen and (max-width: 820px) {
                width: 90%;
                justify-content: center;
            }

        }
        .material-icons {
            margin-right: 8px;
            font-size: 16px;
        }
        .tab-suffix {
            margin-left: 8px;
            color: light-dark(var(--light-muted), var(--dark-muted));
        }
        
    }
</style>
