<template>
    <header>
        <h1>The wonderfull calculator</h1>
    </header>
    <div id="calculator">
        <CalculatorDisplayResult id="resultDisplay" :result="0" />
        <CalculatorButton class="buttons" v-for="button in buttons" :content="button" @click="(content) => buttonClicked(content)" />
    </div>
</template>

<script setup lang="ts">
    import { ref } from 'vue'
    import CalculatorButton from './CalculatorButton.vue'
    import CalculatorDisplayResult from './CalculatorDisplayResult.vue'

    const buttons = ref([
        'C',
        '+/-',
        '%',
        '/',
        '7',
        '8',
        '9',
        'x',
        '4',
        '5',
        '6',
        '-',
        '1',
        '2',
        '3',
        '+',
        '0',
        '.',
        '='
    ])

    function buttonClicked(buttonContent: String) {
        console.log(`Button clicked content: ${buttonContent}`)
    }
</script>

<style scoped>
    #calculator {
        display: flex;
        flex-wrap: wrap;
        width: calc(var(--buttons-size) * var(--buttons-count-row));
    }
    #resultDisplay {
        text-align: center;
        padding: 10px;
        width: calc(var(--buttons-size) * var(--buttons-count-row));
    }
    .buttons:nth-last-child(3) {
        min-width: calc(var(--buttons-size) * 2);
    }
    .buttons {
        min-width: var(--buttons-size);
        min-height: var(--buttons-size);
    }
</style>