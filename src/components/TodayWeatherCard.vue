<template>
    <div class="todayweather-showbox">
        <h1>{{ formData.time }} 日 {{ isMorning? "白天":"夜间" }}</h1>
        <img width="80" height="80" :src="getTianQiIcon(formData.tianQiXQ)"/>
        <div class="wea" title="晴">{{ formData.tianQiXQ }}</div>
        <div class="main-title">
            <span>{{ formData.wenDu }}</span><em>°C</em>
        </div>
        <div class="fengjishu sun-sunUp">
            <img width="20" height="20" src="src/assets/images/风.svg"/>
            <span class="" title="西南风">{{ formData.fengJiShu }}级</span>
        </div>
        <div class="sun-sunUp">
            <img width="20" height="20" src="src/assets/images/日出.svg"/>
            <span>日出</span>
        </div>
        <div class="slid"></div>
    </div>
</template>

<script>
    export default {
        name: "TodayWeatherCard",
        data() {
            return {
                formData: {
                    time: '13',
                    wenDu: '14',
                    fengJiShu: '4-5',
                    tianQiXQ: '雨',
                },
                isMorning: false
            }
        },
        methods: {
            getTianQiIcon(tianQi) {
                switch (tianQi) {
                    case '晴':
                        return "/src/assets/images/晴天.svg";
                    case '雨':
                        return "/src/assets/images/雨天.svg";
                    case '雪':
                        return "/src/assets/images/雪.svg";
                }
            }
        }

    }
</script>

<style lang="scss" scoped>
    .todayweather-showbox {
        margin-left: 5px;
        display: flex;
        flex-direction: column;
        align-items: center;
        border: #dddddd solid 1px;
        width: 150px;
        height: 300px;

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
        color: #7f7f7f;
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
</style>