<template>
    <div class="search-panel">
        <el-row class="m-header-searchbar">
            <el-col
                :span="3"
                class="left"
            >
            <img src="https:/s0.meituan.net/bs/fe-web-meituan/fa5f0f0/img/logo.png" alt="美团"></el-col>
            <el-col
                :span="15"
                class="center"
            >
                <div class="wrapper">
                    <el-input v-model="search" placeholder="搜索商家或地点" @focus="focus" @blur="blur" @input="input"></el-input>
                    <button class="el-button el-button--primary">
                        <i class="el-icon-search"></i>
                    </button>
                    <dl class="hotPlace" v-if="isHoPlace">
                        <dt>热门搜索</dt>
                        <dd v-for="(item, index) in hotPlace" :key="index">{{item}}</dd>
                    </dl>
                    <dl class="searchList" v-if="isSearchList">
                        <dd v-for="(item, index) in serachList" :key="index">{{item}}</dd>
                    </dl>
                </div>
                <p class="suggest">
                    <a href="#">故宫博物院</a>
                    <a href="#">故宫博物院</a>
                    <a href="#">故宫博物院</a>
                    <a href="#">故宫博物院</a>
                </p>
                <ul class="nav">
                    <li><nuxt-link class="takeout" to="/">美团外卖</nuxt-link></li>
                    <li><nuxt-link class="movie" to="/">猫眼电影</nuxt-link></li>
                    <li><nuxt-link class="hotel" to="/">美团酒店</nuxt-link></li>
                    <li><nuxt-link class="apertment" to="/">民宿/公寓</nuxt-link></li>
                    <li><nuxt-link class="business" to="/">商家入驻</nuxt-link></li>
                </ul>
            </el-col>
            <el-col
                :span="6"
                class="right"
            >
                <ul class="security">
                    <li><i class="refund"></i><p class="txt">随时退</p></li>
                    <li><i class="single"></i><p class="txt">不满意退</p></li>
                    <li><i class="overdue"></i><p class="txt">过期退</p></li>
                </ul>
            </el-col>
        </el-row>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                isFocus: false,
                search: '',
                hotPlace: [],
                serachList: []
            }
        },
        methods: {
            focus() {
                this.isFocus = true
            },
            blur() {
                setTimeout(() => {
                    this.isFocus = false
                }, 200)
            },
            input() {
                
            }
        },
        computed: {
            isHoPlace() {
                return this.isFocus && !this.search
            },
            isSearchList() {
                return this.isFocus && this.search
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>