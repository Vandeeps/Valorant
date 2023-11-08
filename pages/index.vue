<script setup>

</script>

<template>
    <title>Valorant API</title>
    <v-theme-provider theme="dark" with-background>
        <v-img src="/bg.jpg" cover>
            <v-container class="fill-height">

                <v-row>
                    <v-col sm="6">
                        <menu-card icon="mdi-clipboard-check" title="Todo List" text="Berisi Contoh Todo List"
                            @click="navigateTo('/char')" />

                    </v-col>
                    <v-col>
                        <menu-card icon="mdi-alpha-v-box" title="Valorant API" text="Berisi Penggunaan Valorant API"
                            @click="navigateTo('/agent')" />


                    </v-col>
                </v-row>
            </v-container>
        </v-img>
    </v-theme-provider>
</template>