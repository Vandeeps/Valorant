<script setup>
import { onMounted } from 'vue';

const { data: agents, pending } = useFetch("https://valorant-api.com/v1/agents",
    {
        query: {
            isPlayableCharacter: true,
        },
    })
</script>

<template>
    <title>Valorant Agents</title>
    <h1>Agents</h1>
    <agent-list :agents="agents?.data" />
</template>
