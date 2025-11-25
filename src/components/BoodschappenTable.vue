<script setup>
import { computed, watch } from 'vue';
import { ref } from 'vue';

const shoppingItems = ref([
    { product: 'Brood', price: 1.00, amount: 0, subTotal: 0.00 },
    { product: 'Broccoli', price: 0.99, amount: 0, subTotal: 0.00 },
    { product: 'Krentebollen', price: 1.20, amount: 0, subTotal: 0.00 },
    { product: 'Noten', price: 2.99, amount: 0, subTotal: 0.00 }
])

watch(shoppingItems, (items) => {
    items.forEach(item => {
        item.subTotal = parseFloat((item.amount * item.price).toFixed(2));
    });
}, { deep: true });

let Total = 0.00
</script>

<template>
    <div class="p-4 max-w-4xl mx-auto">
        <div class="border-2 rounded-xl border-white/80 overflow-hidden">
            <table class="w-full bg-slate-900 shadow-2xl">
                <thead class="bg-slate-800 border-b border-zinc-600">
                    <tr>
                        <th class="px-4 py-4 text-left font-semibold text-slate-200">Brood</th>
                        <th class="px-4 py-4 text-left font-semibold text-slate-200">Prijs</th>
                        <th class="px-4 py-4 text-left font-semibold text-slate-200">Aantal</th>
                        <th class="px-4 py-4 text-left font-semibold text-slate-200">Subtottaal</th>
                    </tr>
                </thead>
                <tbody class="divide-y divide-slate-800">
                    <tr class="hover:bg-slate-800/50 transition-colors text-white font-semibold"
                        v-for="(sI) in shoppingItems">
                        <td class="px-4 py-4">{{ sI.product }}</td>
                        <td class="px-4 py-4 text-emerald-400">€{{ sI.price }}</td>
                        <td class="px-4 py-4">
                            <input class="bg-slate-800 border border-slate-600 rounded px-3 w-[100px] py-1 text-white text-center" 
                                   type="number" 
                                   v-model="sI.amount"/>
                        </td>
                        <td class="px-4 py-4 text-emerald-400">€{{ (sI.amount * sI.price).toFixed(2) }}</td>
                    </tr>
                    <tr class="hover:bg-slate-800/50 transition-colors text-white font-semibold">
                        <td class="px-4 py-4">Total</td>
                        <td></td>
                        <td></td>
                        <td class="px-4 py-4 text-emerald-400">€{{ Total }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>