<script setup>
import InputError from "@/Components/InputError.vue";
import InputLabel from "@/Components/InputLabel.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import Table from "@/Components/Table/Table.vue";
import TableDataCell from "@/Components/Table/TableDataCell.vue";
import TableHeaderCell from "@/Components/Table/TableHeaderCell.vue";
import TableRow from "@/Components/Table/TableRow.vue";
import TextInput from "@/Components/TextInput.vue";
import AdminLayout from "@/Layouts/AdminLayout.vue";
import { Head, Link, useForm } from "@inertiajs/vue3";

const form = useForm({
  name: "",
});
</script>

<template>
  <Head title="Create New Permission" />
  <AdminLayout>
    <div class="max-w-7xl mx-auto py-4">
      <div class="mt-6 max-w-8md mx-auto bg-slate-100 shadow-lg rounded-lg p-6">
        <div class="flex pb-5 space-x-3">
          <Link
            :href="route('permissions.index')"
            class="text-white font-semibold bg-indigo-500 hover:bg-indigo-700 rounded px-3 py-2"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="currentColor"
              class="w-6 h-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18"
              />
            </svg>
          </Link>
          <h1 class="text-2xl flex items-center">Create Permission</h1>
        </div>
        <form @submit.prevent="form.post(route('permissions.store'))">
          <div>
            <InputLabel for="name " value="Name" />

            <TextInput
              id="name"
              type="text"
              class="mt-1 block w-full"
              v-model="form.name"
              autofocus
            />

            <InputError class="mt-2" :message="form.errors.name" />
          </div>

          <div class="flex items-center mt-4">
            <PrimaryButton
              :class="{ 'opacity-25': form.processing }"
              :disabled="form.processing"
            >
              Create
            </PrimaryButton>
          </div>
        </form>
      </div>
    </div>
  </AdminLayout>
</template>
