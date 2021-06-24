<template>
    <div class="terminal">
        <img id="hackerman-logo" alt="Hackerman Logo" src="@/assets/hackerman-logo.jpg" />
        <label id="splash-text">Input password as shown</label>
    </div>
</template>

<script>
export default {
    name: "SplashScreen"
};
</script>

<style scoped>
#hackerman-logo {
    width: 55px;
    height: 55px;
}

#splash-text {
    display: block;
}
</style>
