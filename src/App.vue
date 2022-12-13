<script setup lang="ts">
import { reactive } from 'vue';
import DataTable from '@/components/DataTable.vue'
import { DummyData } from "@/data/mock"

const states = reactive({
  showModal: false,
  currentUserId: null
})

const COLUMNS = {
  ID: {
    label: "Id",
    key: "id"
  },
  FNAME: {
    label: "First Name",
    key: "firstname"
  },
  LNAME: {
    label: "Last Name",
    key: "lastname"
  },
  EMAIL: {
    label: "Email",
    key: "email"
  },
  GENDER: {
    label: "Gender",
    key: "gender"
  },
  IPA: {
    label: "Ip Address",
    key: "ipaddress"
  },
  ACTIONS: {
    label: "Actions",
    key: "actions"
  }
};

const handleActionClick = (id: any) => {
  states.currentUserId = id;
  states.showModal = true;
}

</script>

<template>
  <v-app>
    <v-main>
      <data-table :data="DummyData" :config="[
        {
          title: COLUMNS.ID,
          render: (data) => data.id,
          sortable: true
        },
        {
          title: COLUMNS.FNAME,
          render: (data) => data.fname,
          sortable: true
        },
        {
          title: COLUMNS.LNAME,
          render: (data) => data.lname,
          sortable: true
        },
        {
          title: COLUMNS.EMAIL,
          render: (data) => data.email,
          sortable: true
        },
        {
          title: COLUMNS.GENDER,
          render: (data) => data.gender,
          sortable: true
        },
        {
          title: COLUMNS.IPA,
          render: (data) => data.ipa,
          sortable: true
        },
        {
          title: COLUMNS.ACTIONS
        }
      ]">
        <template #actions="{ data }">
          <v-icon class="me-5" @click="handleActionClick(data.id)">mdi-pencil</v-icon>
          <v-icon class="pointer" @click="handleActionClick(data.id)">mdi-delete</v-icon>
        </template>
      </data-table>
      <v-snackbar v-model="states.showModal">
        User Id {{ states.currentUserId }}
        <template v-slot:actions>
          <v-btn color="pink" variant="text" @click="states.showModal = false">
            Close
          </v-btn>
        </template>
      </v-snackbar>
    </v-main>
  </v-app>
</template>