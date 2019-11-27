<template>
    <div class="m-menu">
        <dl class="nav" @mouseleave="mouseLeave">
            <dt>全部分类</dt>
            <dd v-for="(item, index) in menu" :key="index" @mouseenter="mouseEnter"><i :class="item.type"></i>{{item.name}}<span class="arrow"></span></dd>
        </dl>
        <div class="detail" v-if="kind" @mouseenter="sover" @mouseleave="sout">
            <template v-for="(item, index) in curDetail">
                <h4 :key="index">标题</h4>
                <span v-for="v in item.child" :key="v" :title="v">{{v}}</span>
            </template>
            
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                kind: '',
                menu: [
                    {
                        type: 'food',
                        name: '美食',
                        child: [{
                            title: '美食',
                            child: [
                                '代金券'
                            ]
                        }]
                    }
                ],
                timer: null
            }
        },
        computed: {
            curDetail() {
                return this.menu.find((item) => item.type == this.kind) ? this.menu.find((item) => item.type == this.kind).child : []
            }
        },
        methods: {
            mouseLeave() {
                this.timer = setTimeout(() => {
                    this.kind = ''
                }, 150)
            },
            mouseEnter(e) {
                this.kind = e.target.querySelector('i').className
            },
            sover() {
                clearTimeout(this.timer)
                this.timer = null
            },
            sout() {
                this.kind = ''
            }
        }
    }
</script>

<style lang="scss" scoped> 
</style>