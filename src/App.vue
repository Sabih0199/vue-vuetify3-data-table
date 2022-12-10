<template>
  <v-app>
    <v-main>
      <data-table :data="CategoryManagementData" :config="[
        {
          title: COLUMNS.COURSE_NAME,
          render: (data: { categoryname: String, }) => data.categoryname
        },
        {
          title: COLUMNS.TOTAL_COURSES,
          render: (data: { totalcourses: Number, }) => data.totalcourses
        },
        {
          title: COLUMNS.TOTAL_INSTRUCTORS,
          render: (data: { totalinstructors: Number, }) => data.totalinstructors
        },
        {
          title: COLUMNS.ACTIONS
        }
      ]">
        <template #Actions="{ data }">
          <v-icon class="pointer me-5">mdi-pencil</v-icon>
          <v-icon class="pointer">mdi-delete</v-icon>
        </template>
      </data-table> </v-main>
  </v-app>
</template>

<script setup lang="ts">
import { render } from 'vue';
import DataTable from '@/components/DataTable.vue'

const COLUMNS = {
  COURSE_NAME: {
    label: "Category Name",
    key: "CategoryName"
  },
  TOTAL_COURSES: {
    label: "Total Courses",
    key: "TotalCourses"
  },
  TOTAL_INSTRUCTORS: {
    label: "Total Instructors",
    key: "TotalInstructors"
  },
  ACTIONS: {
    label: "",
    key: "Actions"
  }
};

const CategoryManagementData = [
  {
    categoryname: "Academics",
    totalcourses: "12",
    totalinstructors: "5"
  },
  {
    categoryname: "Art & Design",
    totalcourses: "05",
    totalinstructors: "6"
  },
  {
    categoryname: "Business",
    totalcourses: "10",
    totalinstructors: "2"
  },
  {
    categoryname: "Development",
    totalcourses: "25",
    totalinstructors: "5"
  },
  {
    categoryname: "Finance & Accounting",
    totalcourses: "30",
    totalinstructors: "5"
  },
  {
    categoryname: "Fitness & Health",
    totalcourses: "50",
    totalinstructors: "7"
  },
  {
    categoryname: "It & Software",
    totalcourses: "65",
    totalinstructors: "8"
  },
  {
    categoryname: "Finance & Accounting",
    totalcourses: "30",
    totalinstructors: "5"
  },

  {
    categoryname: "Languages",
    totalcourses: "3",
    totalinstructors: "3"
  },
  {
    categoryname: "Lifestyle",
    totalcourses: "21",
    totalinstructors: "3"
  },
  {
    categoryname: "Marketing",
    totalcourses: "55",
    totalinstructors: "20"
  }
];

</script>
