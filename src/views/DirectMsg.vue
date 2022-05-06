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
                    <button id="new-dm" @click="modalShow = true">
                        <span class="material-icons-outlined"> maps_ugc </span>
                    </button>
                </div>
                <div class="user-list-field">
                    <div
                        v-for="chatItem in this.myChatList"
                        :key="chatItem.cId"
                        :class="curChatIdx === chatItem.cId ? 'user-item now' : 'user-item'"
                        @click="changeChatIdx(chatItem.cId)"
                    >
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
                            <img
                                :src="require(`@/assets/${myChatLog[curChatIdx].profileImg}`)"
                                alt=""
                            />
                        </div>
                        <span class="chat-to-name">{{ myChatLog[curChatIdx].userName }}님</span>
                    </div>
                    <div class="chat-log-field">
                        <div
                            v-for="curMsg in myChatLog[curChatIdx].chatLog"
                            :key="curMsg.mId"
                            :class="
                                curMsg.sendUser === 'me'
                                    ? 'speech-field me'
                                    : 'speech-field to last'
                            "
                        >
                            <div class="reply-story" v-if="curMsg.mType === 'reply'">
                                <div class="line"></div>
                                <span class="msg" v-if="curMsg.sendUser === 'me'"
                                    >스토리에 답장을 보냈습니다.</span
                                >
                                <span class="msg" v-else>회원님의 스토리에 답장을 보냈습니다.</span>
                            </div>
                            <div class="speech-bubble">
                                <div class="img-wrapper" v-if="curMsg.lastMsg">
                                    <img
                                        :src="
                                            require(`@/assets/${myChatLog[curChatIdx].profileImg}`)
                                        "
                                        alt=""
                                    />
                                </div>
                                <span class="msg">{{ curMsg.message }}</span>
                                <div class="got-heart" v-if="curMsg.gotHeart">💖</div>
                            </div>
                        </div>
                    </div>
                    <div class="chat-reply-container">
                        <div class="chat-reply-field">
                            <div class="input-field">
                                <div class="input-content">
                                    <button id="emoji">
                                        <span class="material-icons">sentiment_satisfied_alt</span>
                                    </button>
                                    <input
                                        type="text"
                                        v-model="sendMessage"
                                        placeholder="메시지 입력..."
                                    />
                                    <button id="attach-image" v-if="sendMessage === ''">
                                        <span class="material-icons-outlined"> image </span>
                                    </button>
                                    <button id="send-heart" v-if="sendMessage === ''">
                                        <span class="material-icons-outlined">favorite_border</span>
                                    </button>
                                    <button id="send" v-if="sendMessage !== ''">보내기</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <ModalComp v-if="modalShow" @background-click="bgClick"></ModalComp>
    </section>
</template>

<script>
    import chatListData from '@/assets/data/chatlist.json';
    import chatlogData from '@/assets/data/chatdata.json';
    import ModalComp from '@/components/ModalComp.vue';

    export default {
        name: 'DirectMsg',
        components: { ModalComp },
        props: {},
        data() {
            return {
                sampleData: '',
                myChatList: chatListData,
                myChatLog: chatlogData,
                curChatIdx: 0,
                sendMessage: '',
                modalShow: false,
            };
        },
        setup() {},
        created() {},
        mounted() {},
        unmounted() {},
        methods: {
            changeChatIdx(Idx) {
                this.curChatIdx = Idx;
                this.$router.push(`/direct/inbox/${this.myChatLog[this.curChatIdx].userName}`);
            },

            bgClick() {
                this.modalShow = false;
            },
        },
    };
</script>

<style lang="scss" scoped>
    @import '@/scss/DirectMsg';
</style>
