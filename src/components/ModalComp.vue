<template>
    <div class="full-container" @click.self="backgroundClick">
        <div class="modal-container">
            <slot></slot>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ModalComp',
        components: {},
        data() {
            return {
                sampleData: '',
            };
        },
        setup() {},
        created() {},
        mounted() {
            window.addEventListener('keydown', this.keyHandler);
        },
        unmounted() {
            window.removeEventListener('keydown', this.keyHandler);
        },
        methods: {
            backgroundClick() {
                this.$emit('background-click', true);
            },

            keyHandler(e) {
                if (e.code === 'Escape') this.backgroundClick();
            },
        },
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/ModalComp.scss';
</style>
