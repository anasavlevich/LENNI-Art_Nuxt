<template>
    <div class="app-intro">
        <h1 class="app-intro__title1">арт — пространство</h1>
        <div class="app-intro__pic">
            <SvgIcon class="app-intro__img" name="LENNI" width="1920" height="325" />
        </div>
        <p class="app-intro__title2">
            для людей, горящих сердцем и делом<br />место для настоящего
        </p>
    </div>
</template>

<style lang="less">
.app-intro {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    width: 100%;

    &__title1,
    &__title2 {
        text-align: center;
        text-wrap: nowrap;
        font-family: @font2;
        font-weight: 400;
        font-size: 45px;
        line-height: 1.29;
        text-transform: uppercase;
        @media @bw1660 {
            font-size: 35px;
        }

        @media @bw960 {
            font-size: 30px;
        }

        @media @bw768 {
            font-size: 25px;
        }

        @media @bw600 {
            font-size: 13px;
        }
    }

    &__pic {
        overflow: hidden;
    }

    &__img {
        display: block;
        position: relative;
        width: 100%;
        margin: 0 auto 25px;
        font-size: 0;
        text-decoration: none;

        @media @bw1660 {
            width: 120%;
            margin-left: -11%;
        }

        @media @bw960 {
            width: 150%;
            margin-left: -26%;
        }

        @media @bw768 {
            width: 160%;
            margin-left: -31%;
        }

        @media @bw600 {
            width: 170%;
            margin-left: -36%;
        }
    }

    &__title1 {
        margin-bottom: 70px;

        @media @bw1660 {
            margin-bottom: 0px;
        }

        @media @bw960 {
            margin-bottom: -30px;
        }

        @media @bw768 {
            margin-bottom: -60px;
        }

        @media @bw600 {
            margin-bottom: -80px;
        }

        @media @bw400 {
            margin-bottom: -100px;
        }
    }

    &__title2 {
        margin-top: 70px;
        margin-bottom: 100px;

        @media @bw1660 {
            margin-top: 0px;
        }

        @media @bw960 {
            margin-top: -30px;
            margin-bottom: 70px;
        }

        @media @bw768 {
            margin-top: -60px;
            margin-bottom: 50px;
        }

        @media @bw600 {
            margin-top: -90px;
        }

        @media @bw400 {
            margin-top: -110px;
            margin-bottom: 40px;
        }
    }
}
</style>