<template>
    <div class="todayweather-showbox" :class="getTianQibackGround(formData.tianQiXQ)">
        <h1>{{ getDay() }}日 {{ getWeekTime() }}</h1>
        <img width="60" height="60" :src="getTianQiIcon(formData.tianQiXQ)"/>
        <img v-if="formData.tianQiXQ !== formData.tianQiXQ1" width="60" height="60" :src="getTianQiIcon(formData.tianQiXQ1)"/>
        <div class="wea" title="晴">{{ formData.tianQiXQ }}{{ formData.tianQiXQ !== formData.tianQiXQ1 ? '转'+formData.tianQiXQ1 : ''}}</div>
        <div class="fengjishu sun-sunUp" style="margin-top: 50px">
            {{ formData.zuiGaoWD }} / {{ formData.zuiDiWD }} °C
        </div>
        <div class="fengjishu sun-sunUp">
            <img width="20" height="20" src="src/assets/images/风.svg"/>
            <span class="" title="西南风">{{ formData.fengJiShu }}级</span>
        </div>
        <div class="slid"></div>
    </div>
</template>

<script>
    import moment from 'moment'
    export default {
        name: "qiTianWeather",
        data() {
            return {
                formData: {
                    time: '2021-1-14',
                    wenDu: '14',
                    fengJiShu: '4-5',
                    tianQiXQ: '晴',
                    tianQiXQ1: '雨',
                    zuiGaoWD: '12',
                    zuiDiWD: '0',
                },
                isMorning: false
            }
        },
        methods: {
            getTianQiIcon(tianQi) {
                switch (tianQi) {
                    case '晴':
                        return "/src/assets/images/晴天 (1).svg";
                    case '雨':
                        return "/src/assets/images/雨天.svg";
                    case '雪':
                        return "/src/assets/images/雪.svg";
                }
            },
            getTianQibackGround(tianQi){
                switch (tianQi) {
                    case '晴':
                        return "weather1";
                    case '雨':
                        return "weather2";
                    case '雪':
                        return "weather3";
                }
            },
            getDay(){
              return moment(this.formData.time).format('DD')
            },
            getWeekTime(){
                const time = moment(this.formData.time).day()
                switch (time){
                    case 0:
                        return  "星期日"
                    case 1:
                        return "星期一"
                    case 2:
                        return "星期二"
                    case 3:
                        return "星期三"
                    case 4:
                        return "星期四"
                    case 5:
                        return "星期五"
                    case 6:
                        return "星期六"
                }
            }
        }

    }
</script>

<style lang="scss" scoped>
    .todayweather-showbox {
        color: #ffffff;
        margin-top: 10px;
        margin-left: 5px;
        display: flex;
        flex-direction: column;
        align-items: center;
        border: #dddddd solid 1px;
        width: 150px;
        height: 300px;

        &:hover{
            border: red solid 1px;
        }
        > h1 {
            font-size: 13px;
            margin-top: 14px;
            line-height: 18px;
        }
    }

    .main-title {
        display: flex;
        align-items: flex-end;
        text-align: start;
        font-size: 36px;
        margin-top: 40px;

        > em {
            margin-left: 10px;
            font-size: 24px;
            font-style: normal;
        }
    }

    .fengjishu {
        margin-top: 10px;
    }

    .sun-sunUp {
        display: flex;
        justify-content: center;
        align-items: center;

        > span {
            margin-left: 8px;
        }
    }
    .weather1{
        background:  -webkit-gradient(linear,0% 0,0% 100%,from(#0e7fdf),to(#69b8f0))
    }
    .weather2{
        background:  -webkit-gradient(linear,0% 0,0% 100%,from(#50b2fb),to(#a6d4f6))
    }
    .weather3{
        background:  -webkit-gradient(linear,0% 0,0% 100%,from(#88a9ca),to(#bcd3e3))
    }
</style>