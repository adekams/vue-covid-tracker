<template>
    <div>
        <p class="text-center my-3">{{ footer }}</p>
    </div>
</template>

<script>
export default {
    name: "Header",
    data() {
        return {
            footer: 'Copyright ©2021 Adekams '
        }
    }
}
</script>

<style scoped>
    p {
        font-size: 14px;
    }
</style>