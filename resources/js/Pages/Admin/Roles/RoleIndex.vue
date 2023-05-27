<script setup>
import Table from "@/Components/Table/Table.vue";
import TableDataCell from "@/Components/Table/TableDataCell.vue";
import TableHeaderCell from "@/Components/Table/TableHeaderCell.vue";
import TableRow from "@/Components/Table/TableRow.vue";
import AdminLayout from "@/Layouts/AdminLayout.vue";
import { Head, Link } from "@inertiajs/vue3";

defineProps(["roles"]);
</script>

<template>
  <Head title="Roles" />
  <AdminLayout>
    <div class="max-w-7xl mx-auto py-4">
      <div class="flex justify-between">
        <h1>Roles Index Page</h1>
        <Link
          :href="route('roles.create')"
          class="text-white font-semibold bg-indigo-500 hover:bg-indigo-700 rounded px-3 py-2"
        >
          New Role
        </Link>
      </div>
      <div class="mt-6">
        <Table>
          <template #header>
            <TableHeaderCell>ID</TableHeaderCell>
            <TableHeaderCell>Name</TableHeaderCell>
            <TableHeaderCell>Action</TableHeaderCell>
          </template>
          <template #default>
            <TableRow v-for="role in roles" :key="role.id" class="border-b">
              <TableDataCell>{{ role.id }}</TableDataCell>
              <TableDataCell>{{ role.name }}</TableDataCell>
              <TableDataCell class="space-x-4">
                <Link
                  :href="route('roles.edit', role.id)"
                  class="text-green-400 hover:text-green-600"
                  >Edit</Link
                >
                <Link
                  :href="route('roles.destroy', role.id)"
                  method="DELETE"
                  as="button"
                  class="text-red-400 hover:text-red-600"
                  >Delete</Link
                >
              </TableDataCell>
            </TableRow>
          </template>
        </Table>
      </div>
    </div>
  </AdminLayout>
</template>
