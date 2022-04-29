<template>
    <div class="story-field">
        <div class="story-list-field" :style="`transform: translateX(${-nowPos}px)`">
            <div class="story-item" @click="nextTo(0)"></div>
            <div class="story-item" @click="nextTo(1)"></div>
            <div class="story-item" @click="nextTo(2)"></div>
            <div class="story-item" @click="nextTo(3)"></div>
            <div class="story-item" @click="nextTo(4)"></div>
            <div class="story-item" @click="nextTo(5)"></div>
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
                nowPos: 0,
                curIdx: 0,
            };
        },
        setup() {},
        created() {
            window.addEventListener('keyup', this.keyboardNext);
        },
        mounted() {
            this.nextTo(this.curIdx);
        },
        unmounted() {},
        beforeUnmount() {
            window.removeEventListener('keyup', this.keyboardNext);
        },
        methods: {
            nextTo(idx) {
                let items = document.querySelectorAll('.story-item');
                if (idx < 0 || idx >= items.length) return;

                for (let i = 0; i < items.length; i++) {
                    let item = items[i];

                    if (i !== idx) item.classList.remove('now');
                    else item.classList.add('now');
                }

                this.nowPos =
                    idx * 300 - (document.documentElement.clientWidth - 500) / 2 + idx * 24;
                this.curIdx = idx;
            },

            keyboardNext(e) {
                if (e.code === 'ArrowRight') {
                    this.nextTo(this.curIdx + 1);
                } else if (e.code === 'ArrowLeft') {
                    this.nextTo(this.curIdx - 1);
                }
            },
        },
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/ExplorePage.scss';
</style>
