<template>
    <div class="qita-table">
        <div class="qita-table-row">
            <span class="time">周四（21日）</span><big class="png30 d02"></big>
            <big class="png30 n301"></big>
            <span class="wea">阴转雨</span>
            <span class="tem"><em>16℃</em>/2℃</span>
            <span class="wind">东北风转东风</span>
            <span class="wind1">&lt;3级</span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "QiTaWeatherCard"
    }
</script>

<style lang="scss" scoped>
.qita-table{
    display: flex;
    justify-content: flex-start;
    &-row{
        width: 660px;
        height: 60px;
        display: flex;
        margin-top: 10px;
        border: #dddddd solid 1px;
        justify-content: flex-start;
        &:nth-child(2n){
            background: #f8fcff;
        }
        &:nth-child(2n+1){
            background: #ffffff;
        }
    }
}
</style>