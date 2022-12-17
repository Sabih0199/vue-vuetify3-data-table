<script setup lang="ts">
import { reactive } from 'vue';
import { DataTable } from "vv3-data-table"
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
  AVATAR: {
    label: "Avatar",
    key: "avatar"
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
      <data-table table-class="my-table" pagination-class="my-table-pagination" search-class="my-table-search"
        :data="DummyData" :config="[
          {
            title: COLUMNS.ID,
            render: (data) => data.id,
          },
          {
            title: COLUMNS.AVATAR,
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
        <template #avatar="{ data }">
          <v-avatar :image="data.image" />
        </template>
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

<style lang="scss">
.my-table-search {
  margin: 25px;
}

.my-table-pagination {
  .v-pagination__item {
    &.v-pagination__item--is-active {
      .v-btn {
        background-color: #00cccc;
        color: #fff;
      }
    }
  }
}

.my-table {
  margin: 25px;
  border: 1px solid #eee;
  border-bottom: 2px solid #00cccc;
  box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.10),
    0px 10px 20px rgba(0, 0, 0, 0.05),
    0px 20px 20px rgba(0, 0, 0, 0.05),
    0px 30px 20px rgba(0, 0, 0, 0.05);

  tr {
    td {
      color: #999;
    }

    &:hover {
      background-color: #f4f4f4;

      td {
        color: #555;
      }
    }
  }

  th,
  td {
    border: 1px solid #eee;
  }

  th {
    background-color: #00cccc;
    color: #fff;
    text-transform: uppercase;
  }
}
</style>