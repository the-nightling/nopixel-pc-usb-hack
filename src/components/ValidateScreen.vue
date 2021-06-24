<template>
    <div class="terminal">
        <label v-if="userInput == actualPassword">Success!!!</label>
        <label v-else>Password Input Failed</label>
        
        <div id="compare-div">
            <label>Actual: {{actualPassword}}</label>
            <label>&nbsp;&nbsp;Input: {{userInput}}</label>
        </div>

        <button @click="onClick">Reset</button>
    </div>
</template>

<script>
export default {
    name: "ValidateScreen",
    props: {
        actualPassword: String,
        userInput: String
    },
    methods: {
        onClick() {
            this.$emit("click");
        }
    }
};
</script>

<style scoped>
#compare-div {
    display: flex;
    flex-direction: column;
}
</style>