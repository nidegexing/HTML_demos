<template>
    <div class="wrapper">
        <div class="cube">
            <div class="out-front">前面</div>
            <div class="out-back">后面</div>
            <div class="out-left">左边</div>
            <div class="out-right">右边</div>
            <div class="out-top">上面</div>
            <div class="out-bottom">下面</div>
            <span class="in-front">
                <span class="points">1</span>
            </span>
            <span class="in-back">
                <span class="points">3</span>
                <span class="points pitB2">3</span>
                <span class="points pitB3">3</span>
            </span>
            <span class="in-left">
                <span class="points">2</span>
                <span class="points pitL2">2</span>
            </span>
            <span class="in-right">
                <span class="points">4</span>
                <span class="points">4</span>
                <span class="points">4</span>
                <span class="points">4</span>
            </span>
            <span class="in-top">
                <span class="pitT1">
                    <span class="points">5</span>
                    <span class="points">5</span>
                </span>
                <span class="pitT2">
                    <span class="points">5</span>
                </span>
                <span class="pitT3">
                    <span class="points">5</span>
                    <span class="points">5</span>
                </span>
            </span>
            <span class="in-bottom">
                <span class="points">6</span>
                <span class="points">6</span>
                <span class="points">6</span>
                <span class="points">6</span>
                <span class="points">6</span>
                <span class="points">6</span>
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        name: "TranformDice",
        data() {
            return {

            }
        }
    }
</script>

<style lang="less" scoped>
    .wrapper {
        width: 200px;
        margin: 200px auto;
        perspective: 1000px;

        background-image: linear-gradient(to bottom, #29f9f0 0, #000 80%);
    }

    .wrapper .cube {
        width: 200px;
        height: 200px;
        position: relative;
        /*设置3d环境*/
        transform-style: preserve-3d;
        transform: rotateX(-50deg) rotateY(-50px);
        animation: transform 16s linear infinite;
    }

    @keyframes transform {
        0% {
            transform: rotateX(0) rotateY(0) rotateZ(0);
        }
        100% {
            transform: rotateX(720deg) rotateY(360deg) rotateZ(360deg);
        }
    }

    .cube > div {
        width: 100%;
        height: 100%;
        border: 10px solid #66daff;
        border-radius: 20px;
        position: absolute;
        top: 0;
        color: #ff92ff;
        font-size: 36px;
        font-weight: 100;
        text-align: center;
        line-height: 200px;
        background-color: rgba(51, 51, 51, .3);
    }

    .out-front {
        transform: translateZ(100px);
    }

    .out-back {
        transform: translateZ(-100px);
    }

    .out-left {
        transform: translateX(-100px) rotateY(-90deg);
    }

    .out-right {
        transform: translateX(100px) rotateY(90deg);
    }

    .out-top {
        transform: translateY(-100px) rotateX(90deg);
    }

    .out-bottom {
        transform: translateY(100px) rotateX(-90deg);
    }

    .cube > span {
        display: block;
        width: 90px;
        height: 90px;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-top: -45px;
        margin-left: -45px;
        border: 5px solid #424242;
        border-radius: 30%;
        background-color: #ffe7f9;
        opacity: 0.7;
    }

    .in-front {
        transform: translateZ(45px);
        justify-content: center;
        align-items: center;
    }

    .in-back {
        transform: translateZ(-45px);
    }

    .in-left {
        transform: translateX(-45px) rotateY(-90deg);
    }

    .in-right {
        transform: translateX(45px) rotateY(90deg);
    }

    .in-top {
        transform: translateY(-45px) rotateX(90deg);
    }

    .in-bottom {
        transform: translateY(45px) rotateX(-90deg);
    }

    .points {
        display: block;
        border-radius: 50%;
        width: 20px;
        height: 20px;
        margin: 5px;
        background-color: #bb9aff;
    }

    /* 为1点的父盒子设置 */
    span.in-front {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .in-front > span {
        width: 40px;
        height: 40px;
    }

    /* 为2点的盒子设置 */
    span.in-left {
        display: flex;
        justify-content: center;
    }

    span.in-left > .pitL2 {
        align-self: flex-end;
    }

    .in-left > span {
        width: 25px;
        height: 25px;
        margin: 10px;
    }

    .in-right > span {
        width: 25px;
        height: 25px;
    }

    /* 设置3点的盒子 */
    span.in-back {
        display: flex;
    }

    .in-back .pitB2 {
        align-self: center;
    }

    .in-back .pitB3 {
        align-self: flex-end;
    }

    /* 设置4点的盒子 */
    span.in-right {
        display: flex;
        /* 不设置对齐方式，默认为主轴对齐 */
        /* 换行 */
        flex-wrap: wrap;
    }

    /* 设置5点的盒子 */
    span.in-top {
        display: flex;
    }

    .in-top .pitT1,
    .in-top .pitT3 {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .in-top .pitT2 {
        display: flex;
        align-self: center;
    }

    /* 设置6点的盒子 */
    span.in-bottom {
        display: flex;
        flex-wrap: wrap;
        align-content: space-around;
    }

    .cube:hover .out-front {
        transform: translateZ(200px);

    }

    .cube:hover .out-back {
        transform: translateZ(-200px);
    }

    .cube:hover .out-left {
        transform: translateX(-200px) rotateY(-90deg);
    }

    .cube:hover .out-right {
        transform: translateX(200px) rotateY(90deg);
    }

    .cube:hover .out-top {
        transform: translateY(-200px) rotateX(90deg);
    }

    .cube:hover .out-bottom {
        transform: translateY(200px) rotateX(-90deg);
    }
</style>
