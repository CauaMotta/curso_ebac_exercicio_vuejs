<script setup>
import { reactive, defineProps, watch } from 'vue';

const props = defineProps(['operation'])
const data = reactive({
    numberA: 0,
    numberB: 0,
    signal: '',
    operation: 'plus',
})

function atualizaValor(e) {
    const number = e.currentTarget.value;
    if (e.currentTarget.id === 'a') {
        data.numberA = parseInt(number);
    } else {
        data.numberB = parseInt(number);
    }
}

function calculo() {
    switch (data.operation) {
        case 'plus':
            data.signal = '+';
            return data.numberA + data.numberB;
        case 'minus':
            data.signal = '-';
            return data.numberA - data.numberB;
        case 'divide':
            data.signal = '/';
            return data.numberA / data.numberB;
        case 'multiply':
            data.signal = '*';
            return data.numberA * data.numberB;
        default:
            console.log('deu erro');
            break;
    }
}

watch(() => props.operation, () => data.operation = props.operation)
</script>

<template>
    <div class="d-flex align-items-center">
        <input type="number" id="a" :value="data.numberA" @change="atualizaValor" @keyup="atualizaValor">
        <p class="me-3 ms-3 mb-0 d-inline fs-5">{{ data.signal }}</p>
        <input type="number" id="b" :value="data.numberB" @change="atualizaValor" @keyup="atualizaValor">
        <p class="me-3 ms-3 mb-0 d-inline fs-5">=</p>
        <p class="result d-inline m-0 fs-5">{{ calculo() }}</p>
    </div>
</template>