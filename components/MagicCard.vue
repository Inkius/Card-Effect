<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
    colors: {
        type: Array<string>,
        default: () => ["#ffffff", '#808080']
    },
    size: {
        type: Number,
        default: 1
    },
    opacity: {
        type: Number,
        default: 0.85
    },
    container: {
        type: Object as () => HTMLElement
    }
});

interface MouseMove {
    x: number;
    y: number;
}

const mousePosition: MouseMove = ref({
    x: 0,
    y: 0,
});

function onMouseMove(e: MouseEvent) {
    mousePosition.value.x = e.clientX;
    mousePosition.value.y = e.clientY;
}

</script>
<template>
    <div @mousemove="onMouseMove">
        <div :style="{
            '--mouse-x': `${mousePosition.x}px`,
            '--mouse-y': `${mousePosition.y}px`,
            '--gradient-colors': `${colors.join(', ')}`,
            '--border-size': `${size}px`,
            padding: `var(--border-size)`,
            backgroundImage: `radial-gradient(circle at var(--mouse-x) var(--mouse-y), var(--gradient-colors))`
        }" class="max-w-xs rounded-xl">
            <div :style="{
                '--opacity': `${opacity}`,
                opacity: `var(--opacity)`
            }" class="flex flex-col rounded-lg bg-white">
                <img class="rounded-lg"
                    src="https://ciclovivo.com.br/wp-content/uploads/2018/10/iStock-536613027-630x420.jpg">
                <div class="flex flex-col py-4 px-7 gap-5">
                    <div class="text-sm items-center font-mono flex justify-between">
                        <span>Dezembro 4, 2023</span>
                        <span
                            class="bg-blue-100 text-blue-800 text-xs font-medium me-2 px-2.5 py-0.5 rounded dark:bg-blue-900 dark:text-blue-300">Anime</span>
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
<style scoped></style>
