<template>
    <header>
        <h1>The wonderfull calculator</h1>
    </header>
    <div id="calculator">
        <CalculatorDisplayResult id="resultDisplay" :result="result" />
        <CalculatorButton class="buttons" v-for="button in buttons" :content="button" @click="(content) => buttonClicked(content)" />
    </div>
</template>

<script setup lang="ts">
    import { ref } from 'vue'
    import CalculatorButton from './CalculatorButton.vue'
    import CalculatorDisplayResult from './CalculatorDisplayResult.vue'

    var num1: string = ''
    var num2: string = ''
    var operation: string = '';

    const result = ref(0)

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

    function buttonClicked(buttonContent: string) {
        console.log(`Button clicked content: ${buttonContent}`)
        if(buttonContent.includes("=")) {
            var firstNumber = parseInt(num1)
            var secondNumber = parseInt(num2)
            switch(operation) {
                case "+":
                    result.value = firstNumber + secondNumber
                    break;
                case "-":
                    result.value = firstNumber - secondNumber
                    break;
                case "x":
                    result.value = firstNumber * secondNumber
                    break;
                case "/":
                    result.value = firstNumber / secondNumber
                    break;
                default:
                    break;
            }
            console.log(`Operation ${operation} between ${num1} and ${num2}`);
            
            console.log(`Result of operation: ${result.value}`);
        } else {
            if(/^[^0-9]*$/.test(buttonContent)) {
                console.log(buttonContent);
                operation = buttonContent
            } else {
                if(operation.length == 0) {
                num1 += buttonContent
                } else {
                    num2 += buttonContent
                }
            }
        }
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