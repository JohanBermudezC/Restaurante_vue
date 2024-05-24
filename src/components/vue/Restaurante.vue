<script setup>
import { ref } from 'vue';

const Dias = [
    {
        day: "lunes",
        menu: {
            desayuno: ["Arepa", " pan ", "caldo"],
            almuerzo: ["carne ", "pollo", "caldo"],
            cena: ["Arepa", " pan ", "caldo"]
        }
    },
    {
        day: "martes",
        menu: {
            desayuno: ["Arepa", " pan ", "caldo"],
            almuerzo: ["carne ", "pollo", "caldo"],
            cena: ["Arepa", " pan ", "caldo"]
        }
    },
    {
        day: "miercoles",
        menu: {
            desayuno: ["Arepa", " pan ", "caldo"],
            almuerzo: ["carne ", "pollo", "caldo"],
            cena: ["Arepa", " pan ", "caldo"]
        }
    },
    {
        day: "jueves",
        menu: {
            desayuno: ["Arepa", " pan ", "caldo"],
            almuerzo: ["carne ", "pollo", "caldo"],
            cena: ["Arepa", " pan ", "caldo"]
        }
    },
    {
        day: "viernes",
        menu: {
            desayuno: ["Arepa", " pan ", "caldo"],
            almuerzo: ["carne ", "pollo", "caldo"],
            cena: ["Arepa", " pan ", "caldo"]
        }
    },
    {
        day: "sabado",
        menu: {
            desayuno: ["Arepa", " pan ", "caldo"],
            almuerzo: ["carne ", "pollo", "caldo"],
            cena: ["Arepa", " ewf ", "caldo"]
        }
    }

]

const foods = ref([])
const selectedIndex = ref(0)
const selectedFood = ref('')

function showInfo(i) {
    if (selectedIndex.value == i) {
        selectedIndex.value = -1
    } else {
        selectedIndex.value = i;
    }
}

function showMenu(i) {
    selectedFood.value = i;
    foods.value = []; // Clear the foods list first
    const selectedMenu = Dias[selectedIndex.value].menu[i];

    if (Array.isArray(selectedMenu)) {
        selectedMenu.forEach(food => {
            foods.value.push(food);
        });
    } else {
        foods.value.push(selectedMenu);
    }

}

</script>


<template>

    <div class="mx-auto h-screen flex items-center ">
        <div class="w-2/4  mx-auto flex ">
            <div class="w-2/5 flex flex-col">
                <div v-for="(dia, i) in Dias" :key="i" class="bg-orange-300 mb-1">
                    <h1 @click="showInfo(i)" class="pl-4 hover:cursor-pointer"
                        :class="{ 'bg-slate-500': selectedIndex == i }">{{ dia.day }} </h1>
                </div>

            </div>


            <div class="bg-[#b8d6e0] w-3/5 mb-1">
                <div v-if="selectedIndex !== null">
                    <div class="px-4 mx-12 mt-4 flex space-x-4 text-white">
                        <p v-for="(menu, i) in Dias[selectedIndex].menu" @click="showMenu(i)"
                            :class="{ 'text-[#3b636e] border-b border-black': selectedFood == i }"
                            class="hover:cursor-pointer">
                            <strong>{{ i }}</strong>
                        </p>

                    </div>

                    <div class=" w-auto ml-10 flex flex-col space-y-4 mt-5">

                        <div v-for="(food, i ) in foods" class="flex items-center">
                            <span class="bg-white inline-block w-2 h-2 rounded mr-2"></span>
                            <p> {{ food }}</p>
                        </div>

                    </div>
                </div>
            </div>
        </div>
    </div>

</template>