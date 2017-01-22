<template>
    <div>
        <y-list-container>
            <y-list-item title="Bob" secondaryText="Phone: 13012345678" multi>
                <img src="../assets/avatar.png" slot="img">
            </y-list-item>
            <y-list-item title="分享我的名片" link @click.native="showActionPanel = true"></y-list-item>
            <y-list-item title="设置昵称" link></y-list-item>
        </y-list-container>
        <y-action-sheet type="panel" panelTitle="分享我的名片到" :show="showActionPanel" :actionSheetItem="actionSheetPanelItem"
                        @maskClicked="showActionPanel = false" @close="showActionPanel = false"
                        @cancel="showActionPanel = false">
        </y-action-sheet>
        <y-popup title="分享确认" content="可以在这里传入分享事件回调" :show="shareConfirm" @maskClicked="shareConfirm = false">
            <y-button-group slot="buttonGroup" defaultActiveTabId="1">
                <y-tab-item class="active" title="确认" tabId="1" @click.native="shareConfirm = false"></y-tab-item>
            </y-button-group>
        </y-popup>
    </div>
</template>

<script>
    export default {
        name: 'my',
        components: {},
        data () {
            return {
                showActionPanel: false,
                shareConfirm: false,
                actionSheetPanelItem: [
                    {
                        title: '微信',
                        icon: require('../assets/wechat.png'),
                        callback: this.shareCard
                    },
                    {
                        title: '朋友圈',
                        icon: require('../assets/moment.png'),
                        callback: this.shareCard
                    },
                    {
                        title: 'QQ',
                        icon: require('../assets/qq.png'),
                        callback: this.shareCard
                    },
                    {
                        title: 'QQ空间',
                        icon: require('../assets/qzone.png'),
                        callback: this.shareCard
                    }
                ]
            }
        },
        methods: {
            shareCard: function () {
                console.log('share')
                this.showActionPanel = false
                this.shareConfirm = true
            }
        }
    }
</script>

<style>
</style>
