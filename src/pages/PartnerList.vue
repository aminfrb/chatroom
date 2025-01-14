<template>
  <q-layout view="hhh lpR fFf">
    <q-header reveal bordered class="bg-primary text-white flex justify-center">
      <q-toolbar>
        <q-toolbar-title class="text-center"> Find your partner </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <partner-card />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { api } from 'boot/axios'
import PartnerCard from 'src/components/PartnerCard.vue'

const users = ref([]) // Store the list of users

// Fetch users when the page is loaded
const fetchUsers = async () => {
  try {
    const response = await api.get('users/') // Call the API
    users.value = response.data.users // Assign the data to the users array
  } catch (error) {
    console.error('Error fetching users:', error)
  }
}

// Use onMounted to call fetchUsers automatically when the page loads
onMounted(() => {
  fetchUsers()
})
</script>
