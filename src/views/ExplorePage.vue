<template>
    <div>
        <div class="test">
            <span>안녕하세요</span>
        </div>

        <div>
            <button @click="modalShow = true">모달 테스트 좀 할게요.....</button>
        </div>

        <div v-if="modalShow" @click.self="modalShow = false" class="modal-container">
            <div class="close-field">
                <button @click="modalShow = false">
                    <span class="material-icons-outlined"> close </span>
                </button>
            </div>

            <div class="nav-btn-container">
                <div class="nav-btn-field">
                    <div class="button-wrapper left">
                        <button>Left</button>
                    </div>
                    <div class="button-wrapper right">
                        <button>Right</button>
                    </div>
                </div>
            </div>

            <div class="box-container">
                <div class="box-field" @click.self="modalShow = false">
                    <div class="content-section">
                        <div class="left-box">
                            <div class="img-wrapper">
                                <img :src="require('@/assets/4.jpg')" loading="lazy" alt="" />
                            </div>
                        </div>
                        <div class="right-box">
                            <div class="top">
                                <div class="top-content">
                                    <div class="img-wrapper">
                                        <img :src="require('@/assets/1.jpg')" alt="" />
                                    </div>
                                    <div class="ele-group">
                                        <span>juhenside</span>
                                        <div class="dot"></div>
                                        <button>팔로우</button>
                                    </div>
                                    <button>
                                        <span class="material-icons-outlined"> more_horiz </span>
                                    </button>
                                </div>
                            </div>
                            <div class="content">
                                <div class="content-inside">
                                    <div class="profile">
                                        <div class="img-wrapper">
                                            <img :src="require('@/assets/1.jpg')" alt="" />
                                        </div>
                                    </div>
                                    <div class="post">
                                        <strong>juhenside</strong>
                                        <span class="post-content">
                                            생각하지도 못한 많은 축하를 받았습니다. 학교 떠난 지
                                            2년이 조금 넘어서도 이렇게까지 많은 축하를 받을 수
                                            있었던 건 제가 대학 생활을 잘 해서가 아니라, 저를 잊지
                                            않고 기억해주는 여러분들 덕임을 알기에 더 행복합니다.<br /><br />

                                            막상 학교를 다닐 땐 너무 바빠서 혼자 다닐 때가 많았다고
                                            생각했는데, 정신없는 졸업식을 마치고 천천히 옛날
                                            사진들을 둘러보니 제 주변엔 항상 누군가가 있었네요.
                                            졸업식 때 찍은 사진들도 역시 둘러보니 몇 장의 사진을
                                            제외하곤 몇백 장 모두가 누군가와 함께 찍은 사진이였구요.
                                            저는 혼자이지 않았고 여러분이 그 시절 곳곳에
                                            남아있었습니다. <br /><br />

                                            4년 내내 강의실 위치를 헷갈렸던 창학관에서도, 별 짓을
                                            다했던 동방에서도, 복작복작 귀엽게 모여 놀던 운동장
                                            동아리실, 더럽게 긴 향학로, 학교 내에 뭐 이런 곳이 다
                                            있나 싶었던 숲길, 냄새만 빼면 다 좋았던 붕어방, 거의
                                            살다시피한 일학에서도 모두 여러분이 있었네요. 덕분에
                                            소소하고 재미난 에피소드가 많았습니다. <br /><br />

                                            그동안의 추억을 뒤로 하며 4년 동안의 제 영화가 엔딩
                                            크레딧을 맞게 되었습니다. 그렇지만 아직 제 카메라 롤은
                                            끝나지 않은 것 같아요. 더 소중하고 더 행복한 날들을
                                            만들기 위해 부지런히 담아볼게요. 축하해주셔서
                                            감사했습니다. <br /><br />

                                            - 복무 중에 졸업한 공익 김주현 올림. <br /><br />
                                            생각하지도 못한 많은 축하를 받았습니다. 학교 떠난 지
                                            2년이 조금 넘어서도 이렇게까지 많은 축하를 받을 수
                                            있었던 건 제가 대학 생활을 잘 해서가 아니라, 저를 잊지
                                            않고 기억해주는 여러분들 덕임을 알기에 더 행복합니다.<br /><br />

                                            막상 학교를 다닐 땐 너무 바빠서 혼자 다닐 때가 많았다고
                                            생각했는데, 정신없는 졸업식을 마치고 천천히 옛날
                                            사진들을 둘러보니 제 주변엔 항상 누군가가 있었네요.
                                            졸업식 때 찍은 사진들도 역시 둘러보니 몇 장의 사진을
                                            제외하곤 몇백 장 모두가 누군가와 함께 찍은 사진이였구요.
                                            저는 혼자이지 않았고 여러분이 그 시절 곳곳에
                                            남아있었습니다. <br /><br />

                                            4년 내내 강의실 위치를 헷갈렸던 창학관에서도, 별 짓을
                                            다했던 동방에서도, 복작복작 귀엽게 모여 놀던 운동장
                                            동아리실, 더럽게 긴 향학로, 학교 내에 뭐 이런 곳이 다
                                            있나 싶었던 숲길, 냄새만 빼면 다 좋았던 붕어방, 거의
                                            살다시피한 일학에서도 모두 여러분이 있었네요. 덕분에
                                            소소하고 재미난 에피소드가 많았습니다. <br /><br />

                                            그동안의 추억을 뒤로 하며 4년 동안의 제 영화가 엔딩
                                            크레딧을 맞게 되었습니다. 그렇지만 아직 제 카메라 롤은
                                            끝나지 않은 것 같아요. 더 소중하고 더 행복한 날들을
                                            만들기 위해 부지런히 담아볼게요. 축하해주셔서
                                            감사했습니다. <br /><br />

                                            - 복무 중에 졸업한 공익 김주현 올림. <br /><br />
                                        </span>
                                    </div>
                                </div>
                            </div>
                            <div class="tool">
                                <div class="top-btn-field">
                                    <button>
                                        <span class="material-icons-outlined">
                                            favorite_border
                                        </span>
                                    </button>
                                    <button>
                                        <span class="material-icons-outlined"> chat </span>
                                    </button>
                                    <button>
                                        <span class="material-icons-outlined"> send </span>
                                    </button>
                                    <button>
                                        <span class="material-icons-outlined">
                                            bookmark_border
                                        </span>
                                    </button>
                                </div>
                                <div class="like-field">
                                    <div class="profile-list">
                                        <div class="img-wrapper">
                                            <img :src="require('@/assets/2.jpg')" alt="" />
                                        </div>
                                        <div class="img-wrapper">
                                            <img :src="require('@/assets/3.jpg')" alt="" />
                                        </div>
                                        <div class="img-wrapper">
                                            <img :src="require('@/assets/4.jpg')" alt="" />
                                        </div>
                                    </div>
                                    <span>
                                        <strong>wooong_gill</strong>님 외 <strong>여러 명</strong>이
                                        좋아합니다.
                                    </span>
                                </div>
                            </div>
                            <div class="comment">
                                <div class="comment-inside">
                                    <button>
                                        <span class="material-icons-outlined">
                                            sentiment_satisfied_alt
                                        </span>
                                    </button>
                                    <input type="text" name="" id="" placeholder="댓글 달기..." />
                                    <button>게시</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
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
