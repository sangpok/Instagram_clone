<template>
    <router-view />
</template>

<script>
    export default {
        mounted() {
            document.addEventListener('scroll', this.changeScrollTop);
        },
        methods: {
            changeScrollTop() {
                document.documentElement.style.setProperty(
                    '--now-scroll-top',
                    `-${window.scrollY}px`
                );
            },
        },
    };
</script>

<style lang="scss">
    @import '@/scss/variables';
    @import '@/scss/common';
    @import '@/scss/onboarding';
</style>
