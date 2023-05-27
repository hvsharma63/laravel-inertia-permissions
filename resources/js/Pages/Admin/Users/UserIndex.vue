<script setup>
import Table from "@/Components/Table/Table.vue";
import TableDataCell from "@/Components/Table/TableDataCell.vue";
import TableHeaderCell from "@/Components/Table/TableHeaderCell.vue";
import TableRow from "@/Components/Table/TableRow.vue";
import AdminLayout from "@/Layouts/AdminLayout.vue";
import { Head, Link } from "@inertiajs/vue3";

defineProps(["users"]);
</script>

<template>
  <Head title="Users" />
  <AdminLayout>
    <div class="max-w-7xl mx-auto py-4">
      <div class="flex justify-between">
        <h1>Users Index Page</h1>
        <Link
          :href="route('users.create')"
          class="text-white font-semibold bg-indigo-500 hover:bg-indigo-700 rounded px-3 py-2"
        >
          New User
        </Link>
      </div>
      <div class="mt-6">
        <Table>
          <template #header>
            <TableHeaderCell>ID</TableHeaderCell>
            <TableHeaderCell>Name</TableHeaderCell>
            <TableHeaderCell>Email</TableHeaderCell>
            <TableHeaderCell>Action</TableHeaderCell>
          </template>
          <template #default>
            <TableRow v-for="user in users" :key="user.id" class="border-b">
              <TableDataCell>{{ user.id }}</TableDataCell>
              <TableDataCell>{{ user.name }}</TableDataCell>
              <TableDataCell>{{ user.email }}</TableDataCell>
              <TableDataCell>Edit/Delete</TableDataCell>
            </TableRow>
          </template>
        </Table>
      </div>
    </div>
  </AdminLayout>
</template>
