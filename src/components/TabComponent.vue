<script setup>
    import DetailsPanel from './DetailsPanel.vue';
    import AgreementsPanel from './AgreementsPanel.vue';
    import AssortmentPanel from './AssortmentPanel.vue';
    import CertificatesPanel from './CertificatesPanel.vue';
    import QuestionnairesPanel from './QuestionnairesPanel.vue';

    const model = defineModel()

</script>

<template>
    <div class="tab-panel">
        <DetailsPanel v-if="model === 'details'"></DetailsPanel>
        <AgreementsPanel v-if="model === 'agreements'"></AgreementsPanel>
        <AssortmentPanel v-if="model === 'assortment'"></AssortmentPanel>
        <CertificatesPanel v-if="model === 'certificates'"></CertificatesPanel>
        <QuestionnairesPanel v-if="model === 'questionnaires'"></QuestionnairesPanel>
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
