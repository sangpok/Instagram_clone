<template>
    <section id="story-page">
        <header>
            <div id="logo" @click="close">instagram</div>
            <button id="close" @click="close">
                <span class="material-icons-outlined md-36 md-light"> close </span>
            </button>
        </header>

        <section id="story-list-field">
            <div class="story-item-field">
                <button id="prev">
                    <span class="material-icons md-28 md-light"> arrow_circle_left </span>
                </button>
                <div class="story-content">
                    <div class="content-src">
                        <img src="@/assets/3.jpg" alt="" />
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
                                    <img :src="require(`@/assets/1.jpg`)" />
                                </div>
                                <span id="username">omen.mov</span>
                                <span id="upload-date">10시간 전</span>
                            </div>
                            <div class="ele-group">
                                <span class="friendonly">친한 친구</span>
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
                                :placeholder="this.userName + '님에게 답장하기...'"
                                @focus="ndApply = true"
                                @blur="ndApply = false"
                                @input="showEmoji"
                            />
                            <button id="like" v-if="!ndApply">
                                <span class="material-icons md-28 md-light"> favorite_border </span>
                            </button>
                            <button id="dm" v-if="!ndApply">
                                <span class="material-icons md-28 md-light"> send </span>
                            </button>
                        </div>
                    </div>
                </div>
                <button id="next">
                    <span class="material-icons md-28 md-light"> arrow_circle_right </span>
                </button>
            </div>
            <div class="story-item-field">
                <button id="prev">
                    <span class="material-icons md-28 md-light"> arrow_circle_left </span>
                </button>
                <div class="story-content">
                    <div class="content-src">
                        <img src="@/assets/3.jpg" alt="" />
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
                                    <img :src="require(`@/assets/1.jpg`)" />
                                </div>
                                <span id="username">omen.mov</span>
                                <span id="upload-date">10시간 전</span>
                            </div>
                            <div class="ele-group">
                                <span class="friendonly">친한 친구</span>
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
                                :placeholder="this.userName + '님에게 답장하기...'"
                                @focus="ndApply = true"
                                @blur="ndApply = false"
                                @input="showEmoji"
                            />
                            <button id="like" v-if="!ndApply">
                                <span class="material-icons md-28 md-light"> favorite_border </span>
                            </button>
                            <button id="dm" v-if="!ndApply">
                                <span class="material-icons md-28 md-light"> send </span>
                            </button>
                        </div>
                    </div>
                </div>
                <button id="next">
                    <span class="material-icons md-28 md-light"> arrow_circle_right </span>
                </button>
            </div>
        </section>
    </section>
</template>

<script>
    import storylistdata from '@/assets/data/storylist.json';

    export default {
        name: 'StoryPage',
        components: {},
        props: {
            userName: String,
            storyId: String,
        },
        data() {
            return {
                sampleData: '',
                curIndex: 0,
                ndApply: false,
            };
        },
        setup() {},
        created() {},
        mounted() {
            this.printStoryInfo();
            window.addEventListener('keydown', this.keyeventHandler);
        },
        unmounted() {
            window.removeEventListener('keydown', this.keyeventHandler);
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

            keyeventHandler(e) {
                if (e.code === 'Escape') {
                    this.close();
                } else if (e.code === 'ArrowRight') {
                    console.log('Right');
                } else if (e.code === 'ArrowLeft') {
                    console.log('Left');
                }
            },
        },
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/StoryPage.scss';
</style>
