<template>
    <div id="app" class="calculator">
        <h2>Calculadora</h2>
        <div class="display">
        <p>{{ num1 }} {{ operationSymbol }} {{ num2 }} = {{ result }}</p>
        </div>
        <input type="number" v-model.number="num1" placeholder="Primeiro número" class="input"/>
        <input type="number" v-model.number="num2" placeholder="Segundo número" class="input"/>
  
        <select v-model="operation" class="select">
        <option value="add">+</option>
        <option value="subtract">-</option>
        <option value="multiply">*</option>
        <option value="divide">/</option>
        </select>
    </div>
    </template>
  
    <script setup>
    import { ref, computed } from 'vue';

    const num1 = ref(0);
    const num2 = ref(0);
    const operation = ref('add');
  
    const result = computed(() => {
    switch (operation.value) {
        case 'add':
        return num1.value + num2.value;
        case 'subtract':
        return num1.value - num2.value;
        case 'multiply':
        return num1.value * num2.value;
        case 'divide':
        return num2.value !== 0 ? num1.value / num2.value : 'Divisão por zero';
        default:
        return 0;
    }
    });
  
    const operationSymbol = computed(() => {
    switch (operation.value) {
        case 'add':
        return '+';
        case 'subtract':
        return '-';
        case 'multiply':
        return '*';
        case 'divide':
        return '/';
        default:
        return '';
    }
    });
    </script>
  
    <style scoped>
    .calculator {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 2px solid #007BFF;
    border-radius: 10px;
    background-color: #f8f9fa;
    text-align: center;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
  
    .display {
    font-size: 1.5em;
    margin-bottom: 20px;
    padding: 10px;
    background-color: #e9ecef;
    border: 1px solid #007BFF;
    border-radius: 5px;
    }
  
    .input {
    width: calc(50% - 10px);
    margin: 5px;
    padding: 10px;
    font-size: 1em;
    border: 1px solid #007BFF;
    border-radius: 5px;
    }

    .select {
    width: 60px;
    padding: 10px;
    font-size: 1em;
    margin: 5px;
    border: 1px solid #007BFF;
    border-radius: 5px;
    }
    </style>
