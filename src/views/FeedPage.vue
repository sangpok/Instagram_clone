<template>
    <section id="all-container">
        <section id="feed-container">
            <section id="story-field">
                <div id="story-list" :style="`transform: translateX(-${this.storyCurIdx * 80}px)`">
                    <StoryComp
                        v-for="(item, idx) in this.storyList"
                        :key="idx"
                        :item-data="item"
                        @click="showStory(idx)"
                    ></StoryComp>
                </div>
                <button
                    id="prev"
                    @click="slideTo(this.storyCurIdx - 5)"
                    v-show="this.storyCurIdx !== 0"
                >
                    <span class="material-icons md-28 md-light"> arrow_circle_left </span>
                </button>
                <button
                    id="next"
                    @click="slideTo(this.storyCurIdx + 5)"
                    v-show="this.storyCurIdx !== 1"
                >
                    <span class="material-icons md-28 md-light"> arrow_circle_right </span>
                </button>
            </section>

            <section id="feed-list">
                <FeedComp
                    user-name="omen.mov"
                    post-location="greenwich Park"
                    :image-list="[
                        require('@/assets/0.jpg'),
                        require('@/assets/1.jpg'),
                        require('@/assets/2.jpg'),
                        require('@/assets/3.jpg'),
                        require('@/assets/4.jpg'),
                        require('@/assets/5.jpg'),
                        require('@/assets/6.jpg'),
                        require('@/assets/7.jpg'),
                        require('@/assets/8.jpg'),
                    ]"
                />
                <FeedComp
                    user-name="omen.mov"
                    post-location="greenwich Park"
                    :image-list="[
                        require('@/assets/0.jpg'),
                        require('@/assets/1.jpg'),
                        require('@/assets/2.jpg'),
                        require('@/assets/3.jpg'),
                        require('@/assets/4.jpg'),
                        require('@/assets/5.jpg'),
                        require('@/assets/6.jpg'),
                        require('@/assets/7.jpg'),
                        require('@/assets/8.jpg'),
                    ]"
                />
                <FeedComp
                    user-name="omen.mov"
                    post-location="greenwich Park"
                    :image-list="[
                        require('@/assets/0.jpg'),
                        require('@/assets/1.jpg'),
                        require('@/assets/2.jpg'),
                        require('@/assets/3.jpg'),
                        require('@/assets/4.jpg'),
                        require('@/assets/5.jpg'),
                        require('@/assets/6.jpg'),
                        require('@/assets/7.jpg'),
                        require('@/assets/8.jpg'),
                    ]"
                />
            </section>
        </section>
        <aside id="side-container">
            <section id="myprofile-field">
                <div class="img-wrapper">
                    <img :src="require('@/assets/1.jpg')" alt="" srcset="" loading="lazy" />
                </div>
                <div class="info-field">
                    <span class="account-id">ju_hyun.kim</span>
                    <span class="account-name">김 주현</span>
                </div>
                <button id="account-change">전환</button>
            </section>
            <section id="recommend-field">
                <div class="title-field">
                    <span class="recommend-title">회원님을 위한 추천</span>
                    <span class="recommend-all">모두 보기</span>
                </div>
                <div id="recommend-list">
                    <div class="recommend-item">
                        <div class="img-wrapper">
                            <img :src="require('@/assets/6.jpg')" alt="" srcset="" />
                        </div>
                        <div class="info-field">
                            <span class="account-id">hiking_song</span>
                            <span class="account-name">hyeondongee님 외 8명이 팔로우합..</span>
                        </div>
                        <button id="follow-btn">팔로우</button>
                    </div>
                    <div class="recommend-item">
                        <div class="img-wrapper">
                            <img :src="require('@/assets/2.jpg')" alt="" srcset="" />
                        </div>
                        <div class="info-field">
                            <span class="account-id">trueman.gogi</span>
                            <span class="account-name">iam_ig_님 외 3명이 팔로우합니다</span>
                        </div>
                        <button id="follow-btn">팔로우</button>
                    </div>
                    <div class="recommend-item">
                        <div class="img-wrapper">
                            <img :src="require('@/assets/3.jpg')" alt="" srcset="" />
                        </div>
                        <div class="info-field">
                            <span class="account-id">seokho.kang.357</span>
                            <span class="account-name">jihye_bongbong님 외 9명이 팔로우...</span>
                        </div>
                        <button id="follow-btn">팔로우</button>
                    </div>
                    <div class="recommend-item">
                        <div class="img-wrapper">
                            <img :src="require('@/assets/4.jpg')" alt="" srcset="" />
                        </div>

                        <div class="info-field">
                            <span class="account-id">i_so_ng</span>
                            <span class="account-name">8urp3le님 외 6명이 팔로우합니다</span>
                        </div>
                        <button id="follow-btn">팔로우</button>
                    </div>
                    <div class="recommend-item">
                        <div class="img-wrapper">
                            <img :src="require('@/assets/5.jpg')" alt="" srcset="" />
                        </div>

                        <div class="info-field">
                            <span class="account-id">n_m_b_j_h</span>
                            <span class="account-name">회원님을 위한 추천</span>
                        </div>
                        <button id="follow-btn">팔로우</button>
                    </div>
                </div>
            </section>
            <section id="pageinfo-field"></section>
        </aside>
    </section>
</template>

<script>
    import FeedComp from '@/components/FeedComp.vue';
    import StoryComp from '@/components/StoryComp.vue';
    import storydata from '@/assets/data/storydata.json';
    import storylistdata from '@/assets/data/storylist.json';

    export default {
        name: 'FeedPage',
        components: { FeedComp, StoryComp },
        data() {
            return {
                sampleData: '',
                storyCurIdx: 0,
                storyList: Object,
            };
        },
        setup() {},
        created() {},
        mounted() {
            this.getStoryList();
        },
        unmounted() {},
        methods: {
            getStoryList() {
                this.storyList = storydata;
            },

            showStory(idx) {
                // this.$emit('story-click', idx);
                let tmpList = storylistdata;
                console.log(tmpList[idx]);
                this.$router.push({
                    name: 'stories',
                    params: {
                        userName: tmpList[idx].userName,
                        storyId: tmpList[idx].storyList[0].storyId,
                        storyIdx: idx,
                    },
                });
            },

            slideTo(storyIdx) {
                if (storyIdx < 0) storyIdx = 0;
                if (storyIdx > 8 - storyIdx) storyIdx = 1;
                this.storyCurIdx = storyIdx;
            },
        },
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/FeedPage';
</style>
