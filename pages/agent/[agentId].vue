<script setup>
const { agentId } = useRoute().params

const { data: agent, pending } = useLazyFetch(`https://valorant-api.com/v1/agents/${agentId}`)
const selectedDetail = ref("info")

</script>

<template>
    <h1>Valorant Agent Details {{ agentId }}</h1>
    <div>
        <v-btn variant="text" prepend-icon="mdi-arrow-left-bold-box" @click="navigateTo('/agent')">
            Agent List
        </v-btn>
    </div>
    <v-row v-if="agent?.data">
        <v-col>
            Kiri
        </v-col>
        <v-col>
            <div class="d-flex ">
                <v-img :src="agent.data.fullPortraitV2" height="700" cover />
            </div>
        </v-col>
        <v-col class="px-8">
            <div class="d-flex flex-column">
                <div class="">{{ agent.data.role.displayName }}</div>
                <div class="mb-8 text-h2 font-weight-bold text-uppercase">{{ agent.data.displayName }}</div>
            </div>
            <v-row>
                <v-col cols="12">
                    <v-row>
                        <v-col cols=2>
                            <v-card width="64" height="64" color="grey" class="pa-3">
                                <v-img :src="agent.data.role.displayIcon" />
                            </v-card>
                        </v-col>
                        <v-col>
                            <div>{{ agent.data.description }}</div>
                        </v-col>
                    </v-row>
                </v-col>
                <v-col v-for="ability in agent.data.abilities.filter(a => a.slot != 'Passive')" :key="ability.slot"
                    cols="3">
                    <v-card class="pa-3 mb-3" color="grey">
                        <div>{{ ability.slot }}</div>
                        <v-img :src="ability.displayIcon" />
                    </v-card>

                </v-col>
            </v-row>
        </v-col>
    </v-row>

    <pre>
        {{ agent?.data }}
    </pre>
</template>
