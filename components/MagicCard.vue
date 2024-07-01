<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

interface MouseMove {
    x: number;
    y: number;
}

const mousePosition: MouseMove = ref({
    x: 0,
    y: 0,
})

function onMouseMove(e) {
    mousePosition.value.x = e.clientX
    mousePosition.value.y = e.clientY
}

</script>
<template>
    <div @mousemove="onMouseMove">
        <div :style="{
            '--mouse-x': `${mousePosition.x}px`,
            '--mouse-y': `${mousePosition.y}px`,
            backgroundImage: `radial-gradient(circle at var(--mouse-x) var(--mouse-y), #ffffff, #808080)`
        }" class="movearea max-w-xs p-1 rounded-xl bg-red-500">
            <div class="flex flex-col rounded-lg bg-white">
                <img class="rounded-lg"
                    src="https://ciclovivo.com.br/wp-content/uploads/2018/10/iStock-536613027-630x420.jpg">
                <div class="flex flex-col py-4 px-7 gap-5">
                    <div class="text-sm items-center font-mono flex justify-between">
                        <span>Dezembro 4, 2023</span>
                        <span class="border border-black py-1 px-3 rounded-xl">Anime</span>
                    </div>
                    <h3 class="text-xl">
                        Unraveling the Narrative Mastery of Manga
                    </h3>
                    <p class="font-serif">Dive into the captivating world of anime, from its rich history to the latest
                        trends and fan-favorite
                        series...
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>
<style scoped>
.movearea {
    transition: 3s background-image ease;
}
</style>
