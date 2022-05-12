<template>
    <div class="modal-full-container" @click.self="backgroundClick">
        <slot name="outside-left"></slot>
        <div class="modal-container">
            <slot></slot>
        </div>
        <slot name="outside-right"></slot>
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
