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
    <v-theme-provider theme="dark" with-background>
        <v-img src="/bg.jpg" cover>
            <v-container>
                <div>
                    <v-btn variant="text" prepend-icon="mdi-arrow-left-bold-box" @click="navigateTo('/')">
                        Home
                    </v-btn>
                </div>

                <h1>Agent List</h1>
                <agent-list :agents="agents?.data" />
            </v-container>
        </v-img>
    </v-theme-provider>
</template>
