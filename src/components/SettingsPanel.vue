<template>
    <div id="settings-div">
        <label>Time intervals (ms)</label>
        <div>
            <label>Splash screen:&nbsp;&nbsp;</label>
            <input type="number" step="100" min="100" :value="splashScreenInterval" @input="$emit('update:splashScreenInterval', $event.target.value)" />
        </div>
        <div>
            <label>Display screen:&nbsp;</label>
            <input type="number" step="100" min="100" :value="displayPasswordInterval" @input="$emit('update:displayPasswordInterval', $event.target.value)" />
        </div>
        <div>
            <label>Input screen:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</label>
            <input type="number" step="100" min="100" :value="inputInterval" @input="$emit('update:inputInterval', $event.target.value)" />
        </div>
        <button @click="resetDefaults">Default</button>
    </div>
</template>

<script>
export default {
    name: "SettingsPanel",
    props: {
        splashScreenInterval: null,
        displayPasswordInterval: null,
        inputInterval: null
    },

    methods: {
        resetDefaults() {
            this.$emit('update:splashScreenInterval', 2000);
            this.$emit('update:displayPasswordInterval', 3000);
            this.$emit('update:inputInterval', 7000);
        }
    }
};
</script>

<style scoped>
#settings-div {
    background-color:#3d444e;
    position:absolute;
    bottom: 0%;
    left: 0%;
    display: flex;
    flex-direction: column;
    color: white;
}

input {
    color: white;
    background-color: #3d444e;
    caret-color: white;
    width: 50px;
}
</style>