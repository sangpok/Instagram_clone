<template>
    <!-- <div>
        {{ this.$route.params.userName }}
    </div> -->

    <div id="profile-page">
        <div class="full-container">
            <div class="profile-container">
                <div class="profile-image-container">
                    <div class="img-wrapper">
                        <img :src="require('@/assets/1.jpg')" alt="" />
                    </div>
                </div>
                <div class="profile-info-container">
                    <div class="ele-group">
                        <span id="profile-username">juhenside</span>
                        <button id="send-message">메시지 보내기</button>
                        <button id="follow-user">팔로우</button>
                        <button id="more-menu">
                            <span class="material-icons-outlined"> more_horiz </span>
                        </button>
                    </div>
                    <div class="ele-group">
                        <span>게시물 <strong>291</strong></span>
                        <span>팔로워 <strong>79</strong></span>
                        <span>팔로우 <strong>49</strong></span>
                    </div>
                    <div class="ele-group">
                        <span id="description">
                            𝙅𝙪𝙝𝙚𝙣𝙎𝙞𝙙𝙚 · 제 주변의 여러분들을 담아요. <br />드디어 만든 사진 계정
                        </span>
                    </div>
                    <div class="ele-group">
                        <span
                            ><strong>100._.d</strong>, <strong>you_andme.1230</strong>,
                            <strong>hwajomi</strong>님 외 27명이 팔로우합니다</span
                        >
                    </div>
                </div>
            </div>
            <div class="nav-menu">
                <div class="menu-item now">
                    <div class="menu-content">
                        <span class="material-icons-outlined"> grid_on </span>
                        <span class="description">게시물</span>
                    </div>
                </div>
                <div class="menu-item">
                    <div class="menu-content">
                        <span class="material-icons-outlined"> local_offer </span>
                        <span class="description">태그됨</span>
                    </div>
                </div>
            </div>
            <div class="feed-section">
                <div class="feed-container">
                    <div class="item-container" @click="feedItemClick(0)">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/1.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="item-container">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/2.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="item-container">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/3.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="item-container">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/4.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="item-container">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/5.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="item-container">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/6.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="item-container">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/7.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="item-container">
                        <div class="item-content">
                            <div class="item-mark">
                                <span class="material-icons"> queue </span>
                                <!-- <span class="material-icons"> play_arrow </span> -->
                            </div>
                            <div class="img-wrapper">
                                <img :src="require('@/assets/8.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="item-overlay">
                            <div class="item-overlay-content">
                                <div class="ele-group">
                                    <span class="material-icons"> favorite </span>
                                    <span>143</span>
                                </div>
                                <div class="ele-group">
                                    <span class="material-icons-outlined"> chat_bubble </span>
                                    <span>33</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <ModalComp v-if="modalShow" @background-click="bgClick">
            <template v-slot:outside-left>
                <div class="button-field">
                    <button id="left-post">
                        <span class="material-icons"> arrow_circle_left </span>
                    </button>
                </div>
            </template>

            <template v-slot:default>
                <div class="modal-container">
                    <div class="image-field">
                        <div class="button-field">
                            <button id="left-image">
                                <span class="material-icons"> arrow_circle_left </span>
                            </button>
                        </div>
                        <div class="img-wrapper">
                            <div class="image-list">
                                <img :src="require('@/assets/1.jpg')" alt="" />
                                <img :src="require('@/assets/2.jpg')" alt="" />
                                <img :src="require('@/assets/3.jpg')" alt="" />
                                <img :src="require('@/assets/4.jpg')" alt="" />
                                <img :src="require('@/assets/5.jpg')" alt="" />
                                <img :src="require('@/assets/6.jpg')" alt="" />
                                <img :src="require('@/assets/7.jpg')" alt="" />
                                <img :src="require('@/assets/8.jpg')" alt="" />
                            </div>
                        </div>
                        <div class="button-field">
                            <button id="right-image">
                                <span class="material-icons"> arrow_circle_left </span>
                            </button>
                        </div>
                    </div>
                    <div class="description-field">
                        <div class="feed-user-field"></div>
                        <div class="feed-content-field"></div>
                        <div class="feed-footer"></div>
                        <div class="feed-comment-field"></div>
                    </div>
                </div>
            </template>

            <template v-slot:outside-right>
                <div class="button-field">
                    <button id="right-post">
                        <span class="material-icons"> arrow_circle_right </span>
                    </button>
                </div>
            </template>
        </ModalComp>
    </div>
</template>

<script>
    import ModalComp from '@/components/ModalComp.vue';

    export default {
        name: 'ProfilePage',
        components: { ModalComp },
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
        methods: {
            feedItemClick() {
                this.modalShow = true;
                document.body.classList.add('modal-open');
            },

            bgClick() {
                this.modalShow = false;
                document.body.classList.remove('modal-open');
            },
        },
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/ProfilePage';
</style>
