<template>
    <div class="terminal">
        <button id="start-button" @click="onClick">Start</button>
    </div>
</template>

<script>
export default {
    name: "StartScreen",
    methods: {
        onClick() {
            this.$emit("click");
        }
    }
};
</script>
