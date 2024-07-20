<template>
  <q-page class="">
    <div class="q-pa-md">
      <q-list bordered separator>
        <q-item v-for="entry in entries" :key="entry.id">
          <q-item-section
            class="text-weight-bold"
            :class="useAmountColorClass(entry.amount)"
          >
            {{ entry.name }}
          </q-item-section>

          <q-item-section
            class="text-weight-bold"
            :class="useAmountColorClass(entry.amount)"
            side
          >
            {{ useCurrencify(entry.amount) }}
          </q-item-section>
        </q-item>
      </q-list>
    </div>

    <q-footer>
      <div class="row q-pa-sm q-col-gutter-sm">
        <div class="col">
          <q-input bg-color="white" dense outlined placeholder="Name" />
        </div>
        <div class="col">
          <q-input
            input-class="text-right"
            bg-color="white"
            dense
            outlined
            type="number"
            placeholder="Amount"
            step="0.01"
          />
        </div>
        <div class="col col-auto">
          <q-btn round icon="add" />
        </div>
      </div>
    </q-footer>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from "vue";
import useCurrencify from "src/use/useCurrencify";
import useAmountColorClass from "src/use/useAmountColorClass";

interface Entry {
  id: string;
  name: string;
  amount: number;
}

const entries = ref<Entry[]>([
  {
    id: "1",
    name: "Salary",
    amount: 4999.99,
  },
  {
    id: "2",
    name: "Rent",
    amount: -999,
  },
  {
    id: "3",
    name: "Phone",
    amount: -14.99,
  },
  {
    id: "4",
    name: "Unknown",
    amount: 0,
  },
]);
</script>
