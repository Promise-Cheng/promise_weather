<template>
<div class="card">
    <div class="card-top">
        <div class="card-top-left">
            全国>浙江>杭州>城区
        </div>
        <div class="card-top-right">
            {{ updateTime }}
            <span style="color:#d7d7d7">|</span>
            数据来源 心知天气
        </div>
    </div>
    <div class="card-navs">
        <div class="card-navs-item" :class="isJinTian?'item-active':''" @click="activeChange('jinTian')">
            今天
        </div>
        <div class="card-navs-item" :class="isQiTian?'item-active':''" @click="activeChange('qiTian')">
            7天
        </div>
        <div class="card-navs-item" :class="isQiTa?'item-active':''" @click="activeChange('qiTa')">
            8-15天
        </div>
    </div>
    <div v-show="isJinTian">
        <today-weather></today-weather>
    </div>
    <div v-show="isQiTian">
        <div class="item-inline">
            <template v-for="(item,index) in qiTianData" :key="index">
                <qi-tian-weather></qi-tian-weather>
            </template>
        </div>
    </div>
    <div v-show="isQiTa">
        <qi-ta-weather-card></qi-ta-weather-card>
    </div>
</div>
</template>

<script>
import moment from 'moment'
import TodayWeather from "./TodayWeather.vue";
import QiTianWeather from "./QiTianWeatherCard.vue";
import QiTaWeatherCard from "./QiTaWeatherCard.vue";

export default {
    name: "Card",
    components: {QiTaWeatherCard, QiTianWeather, TodayWeather},
    data() {
        return {
            title: 'test',
            updateTime: '',
            activeName: 'jinTian',
            qiTianData: [
                {},
                {},
                {},
                {},
                {},
                {},
                {},
            ]
        }
    },
    computed:{
      isJinTian(){
          return this.activeName === 'jinTian'
      },
      isQiTian(){
          return this.activeName === 'qiTian'
      },
      isQiTa(){
          return this.activeName === 'qiTa'
      },
    },
    // setup(props,context) {
    //     // 需要解构 prop，可以通过使用 setup 函数中的 toRefs 来安全地完成此操作。
    //     this.updateTime = moment().format('YYYY-MM-DD hh:mm:ss')
    // },
    mounted() {
        this.getList()
    },
    methods:{
        getList(){
            this.updateTime = moment().format('YYYY-MM-DD hh:mm:ss')
        },
        activeChange(key){
            this.activeName = key
        }
    }
}
</script>

<style lang="scss" scoped>
.card {
    padding: 10px;
    height: calc(100vh - 45px);
    background: #ffffff;

    &-top {
        display: flex;
        justify-content: space-between;

        &-right {
            font-size: 13px;
            margin-right: 10px;
            color: #7e7e7e;
        }
    }
    &-navs {
        display: flex;
        justify-content: flex-start;
        flex-direction: row;
        margin-top: 20px;
        height: 32px;
        &-item {
            background: #d0ebff;
            margin-left: 15px;
            width: 132px;
            height: 32px;
            line-height: 32px;
            cursor: pointer;
        }
        .item-active {
            color: #3466bb;
            background: none repeat scroll 0 0 #ecf7ff;
        }
    }
}
    .item-inline{
        display: flex;
        justify-content: flex-start;
    }
</style>