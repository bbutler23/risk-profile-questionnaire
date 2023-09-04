<script setup>
import {ref} from "vue";

const openItem = ref(null);

const accordionData = [
    {
        title: 'How it works',
        points: ['Confirm how closely you agree with 12 statements about your current situation, feelings and attitude to risk.',
            'The answers are converted into a score between 1 and 100.',
            'The score is mapped to one of our seven risk attitude categories. These cover the full range of risk profiles, from very cautious to very adventurous.'
        ],
    },
    {
        title: 'Accordion Item 2',
        points: ['Bullet point 1', 'Bullet point 2'],
    },
];

const toggleItem = (index) => {
    if (openItem.value === index) {
        openItem.value = null;
    } else {
        openItem.value = index;
    }
};

</script>

<template>
    <title>Investor Questionnaire | Wealth At Work</title>
    <div class="text-center">
        <div class="flex w-full pb-3 h-20 bg-gray-500 mt-4 rounded">

        </div>

        <div class="text-center p-4">
            <p class="text-5xl">Risk Profile Questionnaire</p>
        </div>

        <div class="grid place-items-center">
            <div class="w-2/5">
                <ul class="space-y-2">
                    <li v-for="(item, index) in accordionData" :key="index">
                        <button
                            class="w-full border p-2 rounded-lg hover:bg-gray-300 bg-gray-400 focus:outline-none"
                            :class="{ 'bg-gray-100': openItem === index }"
                            @click="toggleItem(index)"
                        >
                            {{ item.title }}
                        </button>
                        <div :class="{ 'hidden': openItem !== index, 'p-2': true }">
                            <ul class="list-disc ml-6 space-y-1">
                                <li v-for="(point, pointIndex) in item.points" :key="pointIndex">{{ point }}</li>
                            </ul>
                        </div>
                    </li>
                </ul>
            </div>
        </div>

        <div class="text-center">
            <div class="max-w-5xl mx-auto p-2 lg:p-8 bg-white h-full">
                <form>
                    <div class="mb-8">
                        <div class="w-full inline-block float-left pt-3 lg:pt-3">
                            <label for="firstname">Firstname</label>
                            <input name="firstname" type="text" class="form-control rounded-full inline-block w-full">
                        </div>

                        <div class="w-full inline-block float-left pt-3 lg:pt-3">
                            <label for="lastname">Lastname</label>
                            <input name="lastname" type="text" class="form-control rounded-full inline-block w-full">
                        </div>

                        <div class="w-full inline-block float-left pt-3 lg:pt-3">
                            <label for="dateOfBirth">Date of birth</label>
                            <input name="dateOfBirth" type="text" class="form-control rounded-full inline-block w-full">
                        </div>
                    </div>

                    <div class="w-full p-6 float-left pt-3 lg:pt-3">
                        <button
                            class="inline-flex items-center px-4 py-2 bg-gray-800 border border-transparent rounded-md
                            font-semibold text-base text-white uppercase tracking-widest hover:bg-gray-700 focus:bg-gray-700
                            active:bg-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 transition ease-in-out duration-150">
                            Start Quiz
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<style scoped>

</style>
