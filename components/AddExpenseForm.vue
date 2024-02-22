<script setup lang="ts">

import { z } from 'zod'
import type { FormSubmitEvent } from '#ui/types'
import { createTools, type Tailwindest } from 'tailwindest'

const tw = createTools<Tailwindest>()

const CATEGORIES = [
  'Food', 'Shop', 'Bill', 'Fun', 'Meds', 'Baby', 'Dog', 'Home', 'Car', 'Backyard', 'Other'
] as const;


const options: { id: number, category: typeof CATEGORIES[number], bg: Tailwindest['backgroundColor'] }[] = [
  { id: 1, category: 'Food', bg: 'bg-red-700' },
  { id: 2, category: 'Shop', bg: 'bg-orange-700', },
  { id: 3, category: 'Bill', bg: 'bg-yellow-700', },
  { id: 4, category: 'Fun', bg: 'bg-lime-700', },
  { id: 5, category: 'Meds', bg: 'bg-green-700', },
  { id: 6, category: 'Baby', bg: 'bg-teal-700', },
  { id: 7, category: 'Dog', bg: 'bg-sky-700', },
  { id: 8, category: 'Home', bg: 'bg-blue-700', },
  { id: 9, category: 'Car', bg: 'bg-violet-700', },
  { id: 10, category: 'Backyard', bg: 'bg-fuchsia-700', },
  { id: 11, category: 'Other', bg: 'bg-pink-700', },
]

const expenseForm = z.object({
  name: z.string().min(4).max(50),
  amount: z.number().positive().max(1_000_000),
  category: z.enum(CATEGORIES)
})

type Schema = z.output<typeof expenseForm>

const state = reactive({
  name: undefined,
  amount: undefined,
  category: undefined
})

async function onSubmit(event: FormSubmitEvent<Schema>) {
  // Do something with data
  console.log(event.data)
}

</script>

<template>
  <UForm :schema="expenseForm" :state="state" class="space-y-4" @submit="onSubmit">
    <UFormGroup label="name" name="name">
      <UInput v-model="state.name" />
    </UFormGroup>

    <UFormGroup label="amount" name="amount">
      <UInput v-model="state.amount" type="number" />
    </UFormGroup>

    <USelectMenu v-model="state.category" :optilons="CATEGORIES" placeholder="Select a category">
      <template #option="{ option: item }">
        {{ }}
        <span class="h-2 w-2 rounded-full" :class="options?.find(op => op.category === item).bg" />
        <span class="truncate">{{ item }}</span>
      </template>
    </USelectMenu>

    {{ JSON.stringify(state) }}


    <UButton type="submit">
      Submit
    </UButton>
  </UForm>
</template>

