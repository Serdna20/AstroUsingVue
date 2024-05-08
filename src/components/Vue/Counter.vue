<script setup>

    import { ref } from 'vue'
    let number = ref(0)
    let time = ref(0)
    let interval

    function add() {
        if (number.value == 0) {
            interval = setInterval(() => {
                time.value++
            }, 1000)
        }

        number.value++

        if (number.value == 100) {
            clearInterval(interval)
        }
    }
    
</script>

<template>
    <section v-show="number > 0" class="float-right bg-red-300 rounded">
        Tiempo: {{time}}
    </section>
    <section @click="add" class="hover:cursor-pointer bg-green-600 text-white py-1 px-2 rounded w-full max-w-6xl text-center mt-10 mx-auto select-none">
        {{number}}      
    </section>
    <p v-if="number == 0" class="bg-yellow-100 px-2 py-1 rounded w-48 text-center mt-4 mx-auto select-none">¿Clickear? ¡O miedo! 👻</p>
    <p v-if="number != 0" class="bg-green-600 px-2 py-1 rounded w-48 text-center mt-4 mx-auto select-none">🔥 Go! Go! Go! 🔥</p>
    <p></p>
</template>