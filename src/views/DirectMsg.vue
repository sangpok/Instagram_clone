<template>
    <section class="container">
        <div class="item">
            <div class="img-wrapper">
                <img :src="require('@/assets/1.jpg')" alt="" />
            </div>
            <div class="elegroup">
                <span class="info1">이름</span>
                <span class="info2">소개글</span>
            </div>
            <button class="btn">버튼</button>
        </div>
        <div class="item">
            <img :src="require('@/assets/2.jpg')" alt="" />
            <div class="elegroup">
                <span class="info1">이름</span>
                <span class="info2">소개글</span>
            </div>
            <button class="btn">버튼</button>
        </div>
        <div class="item">
            <img :src="require('@/assets/3.jpg')" alt="" />
            <div class="elegroup">
                <span class="info1">이름</span>
                <span class="info2">소개글</span>
            </div>
            <button class="btn">버튼</button>
        </div>
        <div class="item">
            <img :src="require('@/assets/5.jpg')" alt="" />
            <div class="elegroup">
                <span class="info1">이름</span>
                <span class="info2">소개글</span>
            </div>
            <button class="btn">버튼</button>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'DirectMsg',
        components: {},
        data() {
            return {
                sampleData: '',
            };
        },
        setup() {},
        created() {},
        mounted() {},
        unmounted() {},
        methods: {},
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/DirectMsg';
</style>
