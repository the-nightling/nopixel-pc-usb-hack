<template>
    <div class=terminal>
        <label id="password-label">{{password}}</label>
    </div>
</template>

<script>
export default {
    name: "PasswordScreen",
    props: {
        password: String
    },

    mounted() {
        this.$emit('mounted', `${Math.random()}`.slice(2, 14));
    }
};
</script>

<style scoped>
#password-label {
    font-size: 38.5px;
}
</style>