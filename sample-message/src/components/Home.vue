<template>
    <div>
        <y-navbar :defaultActiveTabId="navId" @change="navChanged" fixed>
            <y-tab-item tabId="1">未读消息</y-tab-item>
            <y-tab-item tabId="2">已读消息</y-tab-item>
        </y-navbar>
        <div style="padding-top: 52px" v-if="navId == '1'">
            <y-list-container>
                <y-list-item title="Alice" secondaryText="This is a sample text." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Alice" secondaryText="This is a sample text." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Alice" secondaryText="This is a sample text." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Alice" secondaryText="This is a sample text." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Alice" secondaryText="This is a sample text." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
            </y-list-container>
        </div>
        <div style="padding-top: 52px" v-if="navId == '2'">
            <y-list-container>
                <y-list-item title="Bob" secondaryText="I have read the messages." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Bob" secondaryText="I have read the messages." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Bob" secondaryText="I have read the messages." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Bob" secondaryText="I have read the messages." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
                <y-list-item title="Bob" secondaryText="I have read the messages." multi avatar>
                    <img src="../assets/avatar.png" slot="img">
                </y-list-item>
            </y-list-container>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'home',
        components: {},
        data () {
            return {
                navId: '1'
            }
        },
        methods: {
            navChanged: function (tabId) {
                this.navId = tabId
            }
        }
    }
</script>

<style>
</style>
