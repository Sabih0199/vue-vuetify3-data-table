
# Vue Vuetify 3 Data Table

Simple Light Weight Data Table Component.

#### Quick Start:

* Install from npm (https://www.npmjs.com/package/vv3-data-table).
* Clone or [download](https://github.com/Sabih0199/vue-vuetify3-data-table/archive/refs/heads/main.zip) this repo. (if you download, unzip the file to a directory.)
* On the command line in the top directory of this repo, run `npm run dev`
* Visit the application with your browser at http://127.0.0.1:3000/

## Demo

https://joyful-valkyrie-eb30c6.netlify.app


## Features

- Render Jsx Element
- Sorts A-Z
- Pagination
- Style Customization
- Filter By Search
## Usage/Examples

```javascript
<script setup lang="ts">
import { DataTable } from "vv3-data-table"

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
  ACTIONS: {
    label: "Actions",
    key: "actions"
  }
};

const DummyData = [
    {
        id: 1,
        image: "https://robohash.org/harumetodio.png?size=50x50&set=set1",
        fname: "Allan",
        lname: "Malthus",
        email: "amalthus0@odnoklassniki.ru",
    }, 
    {
        id: 2,
        fname: "Fidel",
        image: "https://robohash.org/etenimaliquid.png?size=50x50&set=set1",
        lname: "Micheau",
        email: "fmicheau1@icio.us",
    }, 
    {
        id: 3,
        fname: "Virginie",
        image: "https://robohash.org/molestiasauterror.png?size=50x50&set=set1",
        lname: "Sergeant",
        email: "vsergeant2@com.com",
    }, 
    {
        id: 4,
        fname: "Kristofor",
        image: "https://robohash.org/pariaturodioporro.png?size=50x50&set=set1",
        lname: "Izacenko",
        email: "kizacenko3@github.com",
    }, 
    {
        id: 5,
        fname: "Brittan",
        image: "https://robohash.org/evenietconsequaturaliquam.png?size=50x50&set=set1",
        lname: "Oxshott",
        email: "boxshott4@google.de",
    }
]

</script>

<template>
    <data-table
        :data="DummyData" 
        :config="[
          {
            title: COLUMNS.ID,
            render: (data) => data?.id,
          },
          {
            title: COLUMNS.AVATAR,
          },
          {
            title: COLUMNS.FNAME,
            render: (data) => data?.fname,
            sortable: true
          },
          {
            title: COLUMNS.LNAME,
            render: (data) => data?.lname,
            sortable: true
          },
          {
            title: COLUMNS.EMAIL,
            render: (data) => data?.email,
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
          <v-icon>mdi-pencil</v-icon>
        </template>
      </data-table>
</template>
```
## Badges
[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/Sabih0199/vue-vuetify3-data-table/blob/main/LICENSE)
## Support

https://www.buymeacoffee.com/sabihali


## Authors

- [@Sabih](https://github.com/Sabih0199)
