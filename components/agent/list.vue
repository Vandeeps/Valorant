<script setup>
const Props = defineProps({
    agents: Array
})
</script>

<template>
    <v-row>
        <v-col cols="12" md="3" sm="6" v-for="agent in agents || []" :key="agent.uuid">
            <agent-list-item :agent="agent" />
        </v-col>
    </v-row>
</template>