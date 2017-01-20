<template>
    <div>
        <home v-if="tabId === 'home'"></home>
        <contact v-show="tabId === 'contact'" v-model="contactNumber"></contact>
        <my v-if="tabId === 'my'"></my>
        <y-popup title="欢迎使用Demo" :textList="textListArray" :show="firstLoaded" @maskClicked="firstLoaded = false">
            <img src="./assets/popup-cover.png" slot="cover"/>
            <y-button-group slot="buttonGroup" defaultActiveTabId="2">
                <y-tab-item title="知道了" @click.native="firstLoaded = false" tabId="1"></y-tab-item>
                <y-tab-item class="active" title="了解更多" @click.native="firstLoaded = false" tabId="2"></y-tab-item>
            </y-button-group>
        </y-popup>
        <y-tabbar :defaultActiveTabId="tabId" @change="tabChanged">
            <y-tab-item tabId="home"><i class="iconfont icon-pop" slot="icon"></i>首页</y-tab-item>
            <y-tab-item tabId="contact">
                <i class="iconfont icon-email" slot="icon"></i>
                通讯录
                <y-badge type="text" :text="contactNumber"></y-badge>
            </y-tab-item>
            <y-tab-item tabId="my"><i class="iconfont icon-user" slot="icon"></i>我的</y-tab-item>
        </y-tabbar>
    </div>
</template>

<script>
    import {
        Home,
        Contact,
        My
    } from 'components'
    export default {
        name: 'app',
        data () {
            return {
                tabId: 'home',
                contactNumber: '4',
                firstLoaded: true,
                textListArray: [
                    {
                        content: '本demo展示一些YunUI基础组件的用法'
                    },
                    {
                        content: '更多YunUI组件的用法，请查看官方开放平台文档'
                    },
                    {
                        content: '本demo代码仅供参考学习，如您需要将大段代码用于商业用途，请联系云之家'
                    }
                ]
            }
        },
        created () {
        },
        methods: {
            change (a, b) {
                console.log(a, b)
            },
            tabChanged: function (tabId) {
                this.tabId = tabId
            },
            handleClick: function () {
            }
        },
        components: {
            Home,
            Contact,
            My
        }
    }
</script>

<style>
</style>
