<template>
    <!-- <div>{{ this.$route.params.chatTo }}</div> -->
    <section id="dm-page">
        <div class="container">
            <div class="list-field">
                <div class="tool-field">
                    <div class="account-field">
                        <span id="myaccount">ju_hyun.kim</span>
                        <button id="account-change">
                            <span class="material-icons-outlined"> expand_more </span>
                        </button>
                    </div>
                    <button id="new-dm">
                        <span class="material-icons-outlined"> maps_ugc </span>
                    </button>
                </div>
                <div class="user-list-field">
                    <div v-for="chatItem in this.myChatList" :key="chatItem.cId" class="user-item">
                        <div class="img-wrapper">
                            <img :src="require(`@/assets/${chatItem.profileImg}`)" alt="" />
                        </div>
                        <div :class="chatItem.isNewMsg ? 'message-info new' : 'message-info'">
                            <span class="user-name">{{ chatItem.userName }}님</span>
                            <div class="preview-field">
                                <span class="preview-msg">{{ chatItem.lastMsg }}</span>
                                <span class="receive-time">· {{ chatItem.receivedTime }}</span>
                            </div>
                        </div>
                        <div v-show="chatItem.isNewMsg" class="new-msg">
                            <div class="circle"></div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="main-field">
                <div v-if="this.$route.params.chatTo === undefined" class="onboarding-field">
                    <span class="material-icons-outlined"> forum </span>
                    <span class="info-main">내 메시지</span>
                    <span class="info-sub">친구나 그룹에 비공개 사진과 메시지를 보내보세요.</span>
                    <button id="new-dm-2">메시지 보내기</button>
                </div>

                <div v-else class="chat-field">
                    <div class="chat-to-info">
                        <div class="img-wrapper">
                            <img :src="require(`@/assets/1.jpg`)" alt="" />
                        </div>
                        <span class="chat-to-name">d_hyenii님</span>
                    </div>
                    <div class="chat-log-field">
                        <div class="speech-field me">
                            <div class="speech-bubble">
                                <span class="msg">ㅋㅋㅋ처음엔 뭔가</span>
                            </div>
                        </div>
                        <div class="speech-field to">
                            <div class="speech-bubble">
                                <span class="msg">아 진짜?</span>
                            </div>
                        </div>
                        <div class="speech-field to last">
                            <div class="reply-story">
                                <div class="line"></div>
                                <span class="msg">회원님의 스토리에 답장을 보냈습니다.</span>
                            </div>
                            <div class="speech-bubble">
                                <div class="img-wrapper">
                                    <img :src="require(`@/assets/1.jpg`)" alt="" />
                                </div>
                                <span class="msg">헤헤</span>
                                <div class="got-heart">💖</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import chatListData from '@/assets/data/chatlist.json';
    import chatlogData from '@/assets/data/chatdata.json';

    export default {
        name: 'DirectMsg',
        components: {},
        props: {},
        data() {
            return {
                sampleData: '',
                myChatList: chatListData,
                myChatLog: chatlogData,
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
