<script setup>
const chars = ref([
    {
        id: 1,
        nama: 'Yoru',
        role: "Duelist"
    },
    {
        id: 2,
        nama: 'Reyna',
        role: 'Duelist'
    },
])
const newChar = ref("")
const newRole = ref("")

function handlenNewChar() {
    chars.value.push({
        id: chars.value.length + 1,
        nama: newChar.value,
        role: newRole.value


    })
    newChar.value = ""
    newRole.value = ""
}

function handleDeleteChar(item) {
    chars.value = chars.value.filter(c => c.id != item.id)
}

const selectedChar = ref(null)
function handleSelectChar(item) {
    selectedChar.value = item
    newChar.value = item.nama
    newRole.value = item.role
}

function handleUpdateChar(item) {
    handleDeleteChar(selectedChar.value)

    chars.value.push({
        id: selectedChar.value.id,
        nama: newChar.value,
        role: newRole.value
    })

    newChar.value = ""
    newRole.value = ""
    selectedChar.value = null
}

</script>
<template>
    <!-- <input placeholder="New Characters..." v-model="newChar" />
  <input placeholder="New Characters..." v-model="newRole" /> -->
    <title>Valorant API</title>


    <v-app>

        <v-theme-provider theme="dark" with-background>
            <v-img src="/bg.jpg" cover>
                <p class="text-h2 mb-3 text-center">Valorant Character</p>
                <v-main>
                    <div>
                        <v-btn variant="text" prepend-icon="mdi-arrow-left-bold-box" @click="navigateTo('/')">
                            Home
                        </v-btn>
                    </div>
                    <v-container>

                        <v-text-field class="ml-4 mr-4" variant="solo-filled" label="Character Name : "
                            v-model="newChar"></v-text-field>
                        <v-text-field class="ml-4 mr-4" variant="solo-filled" label="Character Roles : "
                            v-model="newRole"></v-text-field>
                        <v-btn v-if="!selectedChar" color="error" variant="elevated" class="ml-4 mb-3"
                            prepend-icon="mdi-content-save-outline" @click="handlenNewChar()">Save</v-btn>
                        <v-btn v-else="selectedChar" color="error" variant="elevated" class="ml-4 mb-3"
                            prepend-icon="mdi-pencil-outline" @click="handleUpdateChar(item)">Update</v-btn>
                        <v-list>
                            <v-list-item v-for="item in chars" :key="item.id">
                                <div class="d-flex align-center">
                                    <div>{{ item.nama }} - {{ item.role }}</div>
                                    <v-spacer />
                                    <v-btn @click="handleSelectChar(item)" size="small" variant="outlined"
                                        icon="mdi-pencil-outline"></v-btn>
                                    <v-btn @click="handleDeleteChar(item)" size="small" variant="outlined"
                                        icon="mdi-delete-outline"></v-btn>
                                </div>
                            </v-list-item>
                        </v-list>
                    </v-container>
                </v-main>
            </v-img>
        </v-theme-provider>
    </v-app>
</template>
