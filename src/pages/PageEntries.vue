<template>
  <q-page class="">
    <div class="q-pa-md">
      <q-list bordered separator>
        <q-item v-for="entry in entries" :key="entry.id">
          <q-item-section> {{ entry.name }} </q-item-section>

          <q-item-section side> {{ currencify(entry.amount) }} </q-item-section>
        </q-item>
      </q-list>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { computed, ref } from "vue";

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

const currencify = (amount: number): string => {
  let posNegSymbol = "";
  if (amount > 0) posNegSymbol = "+";
  else if (amount < 0) posNegSymbol = "-";

  const currencySymbol = "$",
    amountPositive = Math.abs(amount),
    amountFormatted = amountPositive.toLocaleString("en-US", {
      minimumFractionDigits: 2,
      maximumFractionDigits: 2,
    });

  return `${posNegSymbol} ${currencySymbol} ${amountFormatted}`;
};
</script>
