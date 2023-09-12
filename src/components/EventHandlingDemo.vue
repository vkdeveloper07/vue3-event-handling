<template>
    <!-- inline handlers -->
    <h2>Inline handlers</h2>
    <div class="container">
        <button class="generalbtn" @click="count++">Count++</button>
        <button class="generalbtn" @click="count--">Count--</button>
        <p>{{count}}</p>
    </div>

    <!-- Method handlers -->
    <h2>Method handlers</h2>
    <div class="container">
        <button class="generalbtn" @click="changeText">Change Text</button>
        <button class="generalbtn" @click="resetText">Reset Text</button>
        <p>{{data}}</p>
    </div>
    
    <h2>Accessing Event argument in inline handlers and inline arrow function</h2>
    <div class="container">
        <!-- using $event special variable -->
        <button class="generalbtn" @click="warn('This is an alert using event argument', $event)">Click to given an alert</button>
        <!-- using inline arrow function -->
        <button class="generalbtn" @click="(event) => warn('This is an alert using inline arrow function.', event)">Click to given an alert</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
const count = ref(0);
const data = ref('Text');

function changeText() {
    data.value = 'Vite Vue js 3 app';
}

function resetText() {
    data.value = 'Text';
}

function warn(message, event) {
  // now we have access to the native event
  if (event) {
    event.preventDefault()
  }
  alert(message)
}

</script>

<style scoped>
p {
    display: inline-block;
}
h2 {
    margin: 2%;
}
.container{
    border: 2px solid white;
    margin-top: 2%;
    width: 100%;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
}
.generalbtn{
    margin: 10px;
    padding:5px;
    width: 13%;
}

</style>