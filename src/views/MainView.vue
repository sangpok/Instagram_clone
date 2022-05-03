<template>
    <div id="root" @click="clickHandler">
        <TopHeader
            @notification-click="notificationClick"
            :another-clicked="anotherClicked"
        ></TopHeader>
        <router-view></router-view>
    </div>
</template>

<script>
    import TopHeader from '@/components/TopHeader';

    export default {
        name: 'MainView',
        components: {
            TopHeader,
        },
        data() {
            return {
                sampleData: '',
                anotherClicked: false,
            };
        },
        setup() {},
        created() {},
        mounted() {},
        unmounted() {},
        methods: {
            clickHandler(event) {
                let parentEle = event.target.parentNode.tagName;

                if (this.notificationShow && parentEle.toLowerCase() !== 'button') {
                    if (event.target.className !== 'content') this.anotherClicked = true;
                }
            },
        },
    };
</script>

<style lang="scss" scoped>
    #root {
        position: relative;
    }
</style>
