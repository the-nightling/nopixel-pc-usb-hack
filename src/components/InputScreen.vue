<template>
    <div class="terminal">
        <div id="input-container-div">
            <label id="password-label">Password</label>
            <div id="input-div">
                <img id="hackerman-logo-input" alt="Hackerman Logo" src="@/assets/hackerman-logo.jpg" />
                <input ref="inputRef" :value="text" type="text" @input="$emit('update:text', $event.target.value)" @keyup.enter="$emit('enter')" />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "InputScreen",
    props: {
        text: String
    },
    mounted() {
        this.$nextTick(() => this.$refs.inputRef.focus());
    }
};
</script>

<style scoped>
#input-container-div {
    display: flex;
    flex-direction: column;
}

#input-div {
    display: flex;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    padding-bottom: 2px;
}


#input-div input {
    border: none;
    color: white;
    background-color: #3d444e;
    caret-color: white;
    margin-left: 5px;
}

#input-div input:focus-visible {
    outline: none;
}

#password-label {
    font-size: x-small;
    margin-bottom: 5px;
}

#hackerman-logo-input {
    height: 16px;
    width: 16px;
    align-self: center;
}
</style>