<template>
    <div>
        <button @click="modalShow = true">모달 테스트 좀 할게요.....</button>

        <div v-if="modalShow" @click.self="modalShow = false" class="modal-container">
            <div class="button-field">
                <button>Left</button>
            </div>
            <div class="box-container">
                <div class="left-box">left</div>
                <div class="right-box">right</div>
            </div>
            <div class="button-field">
                <button>Right</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'ExplorePage',
        components: {},
        data() {
            return {
                sampleData: '',
                modalShow: false,
            };
        },
        setup() {},
        created() {},
        mounted() {},
        unmounted() {},
        beforeUnmount() {},
        methods: {},
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/ExplorePage.scss';
</style>
