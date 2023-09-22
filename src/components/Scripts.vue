<template>
    <div id="app">
        <p>{{message}}</p>
    </div>
</template>
<script type="module">
import { createApp, ref, reactive } from 'vue';

// Define the data property using ref or reactive
const app = createApp({
    setup() {
        const message = ref('Hello world');
            // Define methods
        const add = () => {
            count.value++;s
        };
        return {
            message,

            add,
        };
    },
    
});
app.mount('#app');

</script>