<script setup>
import {computed} from 'vue';

const dice = defineModel();

// Count how many times each dice side (1-6) appears
const diceSideCount = computed(() => {
    const counts = [0, 0, 0, 0, 0, 0];
    dice.value.forEach(die => {
        if (die >= 1 && die <= 6) {
            counts[die - 1]++;
        }
    });
    console.log('Dice values:', dice.value);
    console.log('Side counts:', counts);
    return counts;
});

// Upper section scores (Ones through Sixes)
const ones = computed(() => diceSideCount.value[0] * 1);
const twos = computed(() => diceSideCount.value[1] * 2);
const threes = computed(() => diceSideCount.value[2] * 3);
const fours = computed(() => diceSideCount.value[3] * 4);
const fives = computed(() => diceSideCount.value[4] * 5);
const sixes = computed(() => diceSideCount.value[5] * 6);

// Upper section total and bonus
const upperTotal = computed(() => ones.value + twos.value + threes.value + fours.value + fives.value + sixes.value);
const bonus = computed(() => (upperTotal.value >= 63 ? 35 : 0));
const upperSectionTotal = computed(() => upperTotal.value + bonus.value);
const threeOfKindScore = computed(() => {
    return diceSideCount.value.some(count => count >= 3) ? chanceScore.value : 0;
});
const fourOfKindScore = computed(() => {
    return diceSideCount.value.some(count => count >= 4) ? chanceScore.value : 0;
});
const hasFullHouse = computed(() => {
    const countsFiltered = diceSideCount.value.filter(count => count > 0);
    return countsFiltered.includes(3) && countsFiltered.includes(2) ? chanceScore.value : 0;
});
const hasSmallStreet = computed(() => {
    const seq1 =
        diceSideCount.value[0] == 1 &&
        diceSideCount.value[1] == 1 &&
        diceSideCount.value[2] == 1 &&
        diceSideCount.value[3] == 1;
    const seq2 =
        diceSideCount.value[1] == 1 &&
        diceSideCount.value[2] == 1 &&
        diceSideCount.value[3] == 1 &&
        diceSideCount.value[4] == 1;
    const seq3 =
        diceSideCount.value[2] == 1 &&
        diceSideCount.value[3] == 1 &&
        diceSideCount.value[4] == 1 &&
        diceSideCount.value[5] == 1;
    const seq4 =
        diceSideCount.value[3] == 1 &&
        diceSideCount.value[4] == 1 &&
        diceSideCount.value[5] == 1 &&
        diceSideCount.value[6] == 1;
    return seq1 || seq2 || seq3 || seq4 ? 30 : 0;
});
const hasLargeStreet = computed(() => {
    const seq1 =
        diceSideCount.value[0] == 1 &&
        diceSideCount.value[1] == 1 &&
        diceSideCount.value[2] == 1 &&
        diceSideCount.value[3] == 1 &&
        diceSideCount.value[4] == 1;
    const seq2 =
        diceSideCount.value[1] == 1 &&
        diceSideCount.value[2] == 1 &&
        diceSideCount.value[3] == 1 &&
        diceSideCount.value[4] == 1 &&
        diceSideCount.value[5] == 1;
    const seq3 =
        diceSideCount.value[2] == 1 &&
        diceSideCount.value[3] == 1 &&
        diceSideCount.value[4] == 1 &&
        diceSideCount.value[5] == 1 &&
        diceSideCount.value[6] == 1;
    return seq1 || seq2 || seq3 ? 40 : 0;
});
const hasYahtzee = computed(() => {
    return diceSideCount.value.some(count => count == 5) ? 50 : 0;
});
// also functions as return score func for other conditions lowkey
const chanceScore = computed(() => {
    let diceTotal = 0;
    for (let i = 0; i < 6; i++) {
        diceTotal += diceSideCount.value[i] * (i + 1);
    }
    return diceTotal;
});
const lowerSectionTotal = computed(() => {
    return threeOfKindScore.value + fourOfKindScore.value + hasFullHouse.value + hasSmallStreet.value + hasLargeStreet.value + hasYahtzee.value + chanceScore.value
})
const grandTotal = computed(() => {
    return lowerSectionTotal.value + upperSectionTotal.value
})
</script>

<template>
    <div class="bg-white/20 rounded-lg p-4">
        <p class="text-xl font-semibold">Score Table</p>

        <table class="w-full border-collapse">
            <!-- Upper Section -->
            <thead>
                <tr class="border-b-2 border-white/20">
                    <th class="text-left p-2">Category</th>
                    <th class="text-center p-2">Score</th>
                </tr>
            </thead>
            <tbody>
                <!-- Ones -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Ones</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ ones }}</td>
                </tr>
                <!-- Twos -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Twos</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ twos }}</td>
                </tr>
                <!-- Threes -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Threes</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ threes }}</td>
                </tr>
                <!-- Fours -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Fours</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ fours }}</td>
                </tr>
                <!-- Fives -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Fives</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ fives }}</td>
                </tr>
                <!-- Sixes -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Sixes</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ sixes }}</td>
                </tr>
                <!-- Bonus -->
                <tr class="border-b-2 border-white/20 font-semibold">
                    <td class="p-2">Bonus (if ≥ 63)</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ bonus }}</td>
                </tr>
                <!-- Upper Total -->
                <tr class="border-b-2 border-white/20 font-bold">
                    <td class="p-2">Upper Section Total</td>
                    <td class="p-2 text-center bg-zinc-700/50">{{ upperSectionTotal }}</td>
                </tr>

                <!-- Lower Section -->
                <!-- Three of a Kind -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Three of a Kind</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ threeOfKindScore }}</td>
                </tr>
                <!-- Four of a Kind -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Four of a Kind</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ fourOfKindScore }}</td>
                </tr>
                <!-- Full House -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Full House</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ hasFullHouse }}</td>
                </tr>
                <!-- Small Straight -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Small Street</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ hasSmallStreet }}</td>
                </tr>
                <!-- Large Straight -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Large Straight</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ hasLargeStreet }}</td>
                </tr>
                <!-- Yahtzee -->
                <tr class="border-b border-white/10">
                    <td class="p-2">Yahtzee</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ hasYahtzee }}</td>
                </tr>
                <!-- Chance -->
                <tr class="border-b-2 border-white/20">
                    <td class="p-2">Chance</td>
                    <td class="p-2 text-center bg-zinc-800/50">{{ chanceScore }}</td>
                </tr>
                <!-- Lower Total -->
                <tr class="border-b-2 border-white/20 font-bold">
                    <td class="p-2">Lower Section Total</td>
                    <td class="p-2 text-center bg-zinc-700/50">{{ lowerSectionTotal }}</td>
                </tr>
                <!-- Grand Total -->
                <tr class="font-bold text-lg">
                    <td class="p-2">Grand Total</td>
                    <td class="p-2 text-center bg-zinc-600/50">{{ grandTotal }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
