<script setup lang="ts">
import { onMounted, ref } from 'vue';
import { WebViewEvents } from '../../src/core/shared/webviewEvents';

import HelloWorld from './components/HelloWorld.vue';

let isVisible = ref(false);

function toggleVisibility(shouldBeVisible: boolean) {
    isVisible.value = shouldBeVisible;
}

onMounted(() => {
    if (!('alt' in window)) {
        return;
    }

    alt.on(WebViewEvents.toggleVisibility, toggleVisibility);
});
</script>

<template>
    <div :class="isVisible ? {} : { hide: true }">
        <div>
            <a href="https://vitejs.dev" target="_blank">
                <img src="/vite.svg" class="logo" alt="Vite logo" />
            </a>
            <a href="https://vuejs.org/" target="_blank">
                <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
            </a>
        </div>
        <HelloWorld msg="Vite + Vue" />
    </div>
</template>

<style scoped>
.hide {
    display: none !important;
    opacity: 0;
}

.logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
}
.logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
    filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
