<template>
    <section id="story-page">
        <header>
            <div id="logo" @click="close">instagram</div>
            <button id="close" @click="close">
                <span class="material-icons-outlined md-36 md-light"> close </span>
            </button>
        </header>

        <div class="story-field">
            <section id="story-list-field" :style="`transform: translateX(${-nowPos}px)`">
                <div
                    v-for="(storyInfo, i) in listData"
                    :key="i"
                    class="story-item-field"
                    @click="nextTo(i)"
                >
                    <button id="prev">
                        <span class="material-icons md-28 md-light"> arrow_circle_left </span>
                    </button>
                    <div class="story-content">
                        <div class="content-src">
                            <img :src="require(`@/assets/${storyInfo.storyList[0].storyImg}`)" />
                        </div>
                        <div :class="ndApply ? 'content-overlay nd' : 'content-overlay'">
                            <div class="story-timeline">
                                <div class="timeline-item"></div>
                                <div class="timeline-item"></div>
                                <div class="timeline-item now"></div>
                            </div>
                            <div class="story-user-info">
                                <div class="ele-group">
                                    <div class="img-wrapper">
                                        <img :src="require(`@/assets/${storyInfo.profileImg}`)" />
                                    </div>
                                    <span id="username">{{ storyInfo.userName }}</span>
                                    <span id="upload-date">10시간 전</span>
                                </div>
                                <div class="ele-group">
                                    <span
                                        v-if="storyInfo.storyList[0].storyState === 'friend'"
                                        class="friendonly"
                                        >친한 친구</span
                                    >
                                    <button id="play">
                                        <span class="material-icons"> play_arrow </span>
                                    </button>
                                    <button id="volume">
                                        <span class="material-icons"> volume_off </span>
                                    </button>
                                    <button id="more">
                                        <span class="material-icons"> more_horiz </span>
                                    </button>
                                </div>
                            </div>

                            <div class="emoji-field" v-if="ndApply">
                                <div class="emoji-content">
                                    <span>빠른 공감</span>
                                    <div class="emoji-list">
                                        <div class="emoji-item">😂</div>
                                        <div class="emoji-item">😮</div>
                                        <div class="emoji-item">😍</div>
                                        <div class="emoji-item">😢</div>
                                        <div class="emoji-item">👏</div>
                                        <div class="emoji-item">🔥</div>
                                        <div class="emoji-item">🎉</div>
                                        <div class="emoji-item">💯</div>
                                    </div>
                                </div>
                            </div>

                            <div class="story-footer">
                                <input
                                    type="text"
                                    :placeholder="storyInfo.userName + '님에게 답장하기...'"
                                    @focus="ndApply = true"
                                    @blur="ndApply = false"
                                    @input="showEmoji"
                                />
                                <button id="like" v-if="!ndApply">
                                    <span class="material-icons md-28 md-light">
                                        favorite_border
                                    </span>
                                </button>
                                <button id="dm" v-if="!ndApply">
                                    <span class="material-icons md-28 md-light"> send </span>
                                </button>
                            </div>
                        </div>
                        <div v-show="i !== this.curIdx" class="user-profile">
                            <StoryComp :item-data="this.storyData[i]"></StoryComp>
                        </div>
                    </div>
                    <button id="next">
                        <span class="material-icons md-28 md-light"> arrow_circle_right </span>
                    </button>
                </div>
            </section>
        </div>
    </section>
</template>

<script>
    import storylistdata from '@/assets/data/storylist.json';
    import storydata from '@/assets/data/storydata.json';
    import StoryComp from '@/components/StoryComp.vue';

    export default {
        name: 'StoryPage',
        components: { StoryComp },
        props: {
            userName: String,
            storyId: String,
            storyIdx: Number,
        },
        data() {
            return {
                sampleData: '',
                curIndex: 0,
                ndApply: false,
                nowPos: 0,
                curIdx: 0,
                listData: Object,
                storyData: Object,
            };
        },
        setup() {},
        created() {},
        mounted() {
            console.log('mounted');
            this.listData = storylistdata;
            this.storyData = storydata;
            console.log(this.storyData);
            this.curIdx = this.storyIdx * 1;
            this.printStoryInfo();
            this.nextTo(this.curIdx);
            window.addEventListener('keydown', this.keyeventHandler);
        },
        unmounted() {
            window.removeEventListener('keydown', this.keyeventHandler);
        },
        updated() {
            this.nextTo(this.curIdx);
        },
        methods: {
            printStoryInfo() {
                let listData = storylistdata;
                let storyData = null;

                for (let idx = 0; idx < listData.length; idx++) {
                    if (listData[idx].userName === this.userName) {
                        storyData = listData[idx].storyList.filter(
                            (item) => item.storyId === this.storyId
                        )[0];
                        console.log(storyData);
                        this.curIndex = idx;
                    }
                }

                console.log(storyData);
            },

            close() {
                this.$router.push('/main');
            },

            ndToggle() {
                this.ndApply = true;
            },

            nextTo(idx) {
                console.log(idx);
                let items = document.querySelectorAll('.story-item-field');
                console.log(items);
                if (idx < 0 || idx >= items.length) return;

                for (let i = 0; i < items.length; i++) {
                    let item = items[i];

                    if (i !== idx * 1) {
                        item.classList.remove('now');
                    } else {
                        item.classList.add('now');
                    }
                }

                this.nowPos =
                    idx * 250 - (document.documentElement.clientWidth - 500) / 2 + idx * 28;
                this.curIdx = idx;
                console.log(`curIdx: ${this.curIdx}`);
            },

            keyeventHandler(e) {
                if (e.code === 'Escape') {
                    this.close();
                } else if (e.code === 'ArrowRight') {
                    this.nextTo(this.curIdx + 1);
                } else if (e.code === 'ArrowLeft') {
                    this.nextTo(this.curIdx - 1);
                }
            },
        },
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/StoryPage.scss';
</style>
