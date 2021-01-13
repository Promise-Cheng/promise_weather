<template>
    <div class="today-card">
        <div class="today-card-left">
            <div class="today-card-left-top">13:10 实况</div>
            <div class="today-card-left-main">
                <div class="main-title">
                    15 <em>℃</em>
                </div>
                <div class="main-content">
                    <div class="main-content-item">
                        <i class="iconfont iconIOTtubiao_huabanfuben" style="margin-right: 5px"></i> <em>相对湿度</em> <em>19%</em>
                    </div>
                    <div class="main-content-item">
                        <i class="iconfont iconfeng" style="margin-right: 5px"></i> <em>南风</em> <em>3级</em>
                    </div>
                </div>
                <div class="main-content">
                    <div class="main-content-item">
                        <i class="iconfont iconcheliang" style="margin-right: 5px"></i> <em>3和7</em>
                    </div>
                    <div class="main-content-item">
                        <i class="iconfont iconkongqizhiliang" style="margin-right: 5px"></i> <em>64</em>
                    </div>
                </div>
            </div>
        </div>
        <today-weather-card></today-weather-card>
        <today-weather-card></today-weather-card>
    </div>
</template>

<script>

    import TodayWeatherCard from "./TodayWeatherCard.vue";
    export default {
        name: "todayWeather",
        components: {TodayWeatherCard}
    }
</script>

<style lang="scss" scoped>
    .today-card {
        margin: 15px;
        display: flex;
        height: 100%;
        justify-content: flex-start;

        &-left {
            display: flex;
            flex-direction: column;
            color: #ffffff;
            background: url("https://videoshfcx.tianqi.cn/xizang/tqwy_img/wyExtImages/5107_9d6d507c194311e992905cb9018cf0d4.jpg?1610512396")
            center center / 100% 100% no-repeat rgb(0, 0, 0);
            height: 100%;
            padding: 20px;
            width: 460px;

            &-top {
                display: flex;
                justify-content: flex-end;
                height: 20px;
                font-size: 13px;
            }

            &-main {
                flex: 1;
                margin-top: 75px;
                display: flex;
                flex-direction: column;

                .main-title {
                    display: flex;
                    align-items: flex-end;
                    text-align: start;
                    font-size: 70px;

                    > em {
                        margin-left: 10px;
                        font-size: 55px;
                        font-style: normal;
                    }
                }

                .main-content {
                    margin-top: 15px;
                    display: flex;
                    justify-content: flex-start;
                }

                .main-content-item {
                    width: 150px;
                    margin-left: 20px;
                    display: flex;
                    align-items: flex-end;
                    font-size: 16px;
                    text-align: start;

                    > em {
                        margin-left: 10px;
                        font-style: normal;
                    }
                }
            }
        }
    }
</style>