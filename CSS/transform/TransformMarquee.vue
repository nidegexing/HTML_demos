<template>
    <div class="wrapper">
        <ul>
            <li>
                <div class="item-name-container">Kaola1</div>
                <img class="item-name-img" src="/static/image/avator_Kaola.jpg" alt="">
            </li>
            <li>
                <div class="item-name-container">Kaola2</div>
                <img class="item-name-img" src="/static/image/avator_Kaola.jpg" alt="">
            </li>
            <li>
                <div class="item-name-container">Kaola3</div>
                <img class="item-name-img" src="/static/image/avator_Kaola.jpg" alt="">
            </li>
            <li>
                <div class="item-name-container">Kaola4</div>
                <img class="item-name-img" src="/static/image/avator_Kaola.jpg" alt="">
            </li>
            <li>
                <div class="item-name-container">Kaola5</div>
                <img class="item-name-img" src="/static/image/avator_Kaola.jpg" alt="">
            </li>
            <li>
                <div class="item-name-container">Kaola6</div>
                <img class="item-name-img" src="/static/image/avator_Kaola.jpg" alt="">
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "TransformMarquee",
        data() {
            return {
            }
        },
    }
</script>

<style lang="less" scoped>
    .wrapper {
        width: 200px;
        margin: 200px auto;
        perspective: 1000px;

        background-image: linear-gradient(to bottom, #29f9f0 0, #000 80%);

        ul {
            list-style: none;
            width: 200px;
            height: 150px;
            margin: 70px auto;
            /* 父盒子开启3d */
            transform-style: preserve-3d;
            /* 引入动画效果 */
            animation: rotate 18s linear infinite;

            &:hover {
                animation-play-state: paused;
            }
        }

        @keyframes rotate {
            /* 旋转沿x轴旋转-10度,再绕y轴旋转 */
            0% {
                transform: rotateX(-10deg) rotateY(0deg)
            }
            100% {
                transform: rotateX(-10deg) rotateY(360deg)
            }

        }

        ul li {
            /* 绝对定位,先让li标签重叠 */
            position: absolute;
            height: 10rem;
            width: 10rem;

            .item-name-container {
                /* 图片和父盒子一样大 */
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
                background: lightcyan;
            }

            &:hover .item-name-container {
                z-index: 3;
            }

            .item-name-img {
                /* 图片和父盒子一样大 */
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 100%;
            }
        }

        ul li:nth-child(1) {
            /* 先绕y轴旋转60度,再沿z轴平移200px,就会形成立体感 */
            transform: rotateY(60deg) translateZ(200px)
        }

        ul li:nth-child(2) {
            transform: rotateY(120deg) translateZ(200px)
        }

        ul li:nth-child(3) {
            transform: rotateY(180deg) translateZ(200px)
        }

        ul li:nth-child(4) {
            transform: rotateY(240deg) translateZ(200px)
        }

        ul li:nth-child(5) {
            transform: rotateY(300deg) translateZ(200px)
        }

        ul li:nth-child(6) {
            transform: rotateY(360deg) translateZ(200px)
        }
    }
</style>
