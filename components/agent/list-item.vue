<script setup>
const props = defineProps({
    agent: Object
})
</script>

<template>
    <v-card @click="navigateTo(`/agent/${agent.uuid}`)" variant="tonal" class="pa-4 ">
        <div class="d-flex flex-column align-center">
            <v-avatar size="96" :image="agent?.displayIcon" />
            <div class="text-h6 font-weight-bold mt-4">
                {{ agent.displayName }}
            </div>
            <div class="text-medium-emphasis">
                {{ agent?.role?.displayName }}
            </div>
        </div>
    </v-card>
</template>