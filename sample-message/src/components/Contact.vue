<template>
    <div>
        <div v-if="!addMode">
            <y-list-container>
                <y-list-item v-for="people in contacts" :title="people.name" :secondaryText="'Phone: '+ people.phone">
                    <img :src="people.avatar" slot="iconLeft">
                    <i class="iconfont icon-sun" slot="iconRight" v-if="people.star"></i>
                </y-list-item>
            </y-list-container>
        </div>
        <div v-if="addMode">
            <y-form>
                <y-input label="姓名" placeholder="请输入姓名" :defaultValue="name" @change="setName"></y-input>
                <y-input label="Phone" placeholder="请输入电话号码" :defaultValue="phone" @change="setPhone"></y-input>
                <y-switch label="设为重要联系人" @change="setStar"></y-switch>
            </y-form>
            <y-button @click="save">保存</y-button>
        </div>
        <div style="text-align: center" v-if="!addMode">
            <y-button size="middle" @click="addMode = true">添加联系人</y-button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'contact',
        components: {},
        data () {
            return {
                addMode: false,
                name: '',
                phone: '',
                star: false,
                contacts: [
                    {
                        name: 'Alice',
                        phone: '13012345678',
                        star: true,
                        avatar: require('../assets/logo.png')
                    },
                    {
                        name: 'Bob',
                        phone: '13012345678',
                        avatar: require('../assets/logo.png')
                    },
                    {
                        name: 'Cydia',
                        phone: '13012345678',
                        avatar: require('../assets/logo.png')
                    },
                    {
                        name: 'Dickens',
                        phone: '13012345678',
                        avatar: require('../assets/logo.png')
                    }
                ]
            }
        },
        watch: {
            contacts (val) {
                this.$emit('input', val.length.toString())
            }
        },
        methods: {
            setName: function (value) {
                // 姓名表单验证
                if (value) {
                    this.name = value
                } else {
                    this.$toast({
                        content: '输入不能为空'
                    })
                }
            },
            setPhone: function (value) {
                // 电话表单验证
                if (value) {
                    this.phone = value
                } else {
                    this.$toast({
                        content: '输入不能为空'
                    })
                }
            },
            setStar: function (value) {
                this.star = value
            },
            save: function () {
                if (!(this.name && this.phone)) {
                    return this.$toast({
                        content: '输入不能为空!'
                    })
                }
                this.$toast({
                    content: '添加成功',
                    icon: 'success'
                })
                this.contacts.push({
                    name: this.name,
                    phone: this.phone,
                    star: this.star,
                    avatar: require('../assets/logo.png')
                })
                this.addMode = false
                this.star = false
                this.name = ''
                this.phone = ''
            }
        }
    }
</script>

<style>
</style>
