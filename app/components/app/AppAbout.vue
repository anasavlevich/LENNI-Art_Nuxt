<template>
    <section class="app-about">
        <h2 class="app-about__section-title section-title">о нас</h2>
        <div class="app-about__container">
            <div class="app-about__block1">
                <h3 class="app-about__title1">Проект «Millennials»</h3>
                <p class="app-about__text1">
                    Вдохновлен молодыми идейными людьми, увлеченными творчеством, эмоциями и
                    желанием сделать мир лучше, проявить себя. У них есть талант и
                    стремление, у нас возможность помочь им воплотить их мечту в реальность.
                </p>
            </div>
            <div class="app-about__block2">
                <picture class="app-about__picture1">
                    <img src="@/assets/images/about/about_1.jpg" class="app-about__img" alt="about1" />
                </picture>
                <h3 class="app-about__title2">
                    Мы предоставляем площади для вашего мероприятия
                </h3>
                <p class="app-about__text2">
                    И оказываем помощь с организацией, если вам это нужно.<br />Наша цель:
                    вовлечь в культурную жизнь города как можно больше людей, помочь молодым
                    ребятам сделать первые шаги к своей мечте и рассказать всем о том, что
                    их волнует.
                </p>
                <picture class="app-about__picture2">
                    <img src="@/assets/images/about/about_2.jpg" class="app-about__img" alt="about2" />
                </picture>
            </div>
            <div class="app-about__block3">
                <div class="app-about__block3-img">
                    <picture class="app-about__picture3">
                        <img src="@/assets/images/about/about_3.png" class="app-about__img" alt="about3" />
                    </picture>
                </div>
                <p class="app-about__text3">
                    Мы уже успешно организовали и провели более 100 проектов. Посмотрите,
                    как это было классно.
                </p>
                <a href="#" class="app-about__link">
                    <span class="app-about__link-text">Смотреть</span>                    
                    <button type="button" class="app-about__link-arrow arrow">
                        <SvgIcon class="arrow__icon" name="arrow" width="91" height="60" />                        
                    </button>
                </a>
            </div>
        </div>
    </section>
</template>

<style lang="less">
.app-about {
  &__container {
    .container();
  }

  &__section-title {
    @media @bw960 {
      margin-top: -90px;
    }
    @media @bw600 {
      margin-top: -100px;
    }
  }
  &__block1 {
    margin-bottom: 100px;
    display: flex;
    flex-direction: column;
    @media @bw600 {
      margin-bottom: 60px;
    }
  }

  &__block2 {
    display: grid;
    grid-template-columns: 1fr 406px;
    gap: 90px 65px;
    margin-bottom: 75px;
    grid-template-areas:
      "pic1 pic2"
      "title pic2"
      "text text";
    @media @bw960 {
      grid-template-areas:
        "pic1 pic1"
        "title pic2"
        "text pic2";
      grid-template-columns: 55% auto;
    }
    @media @bw700 {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-bottom: 50px;
    }
  }

  &__picture1 {
    grid-area: pic1;
  }

  &__title1,
  &__title2 {
    font-weight: 700;
    font-size: 44px;
    @media @bw960 {
      font-size: 26px;
    }
    @media @bw370 {
      font-size: 16px;
    }
  }

  &__title1 {
    text-wrap: nowrap;
  }

  &__title2 {
    grid-area: title;
    @media @bw960 {
      width: 420px;
    }
    @media @bw700 {
      width: 100%;
      margin-top: -50px;
    }
  }

  &__picture2 {
    grid-area: pic2;
    align-self: flex-end;
    width: 100%;
    @media @bw700 {
      width: 70%;
      margin-top: -50px;
    }
  }

  &__text1,
  &__text2,
  &__text3 {
    width: 100%;
    font-weight: 400;
    font-size: 18px;
    @media @bw960 {
      font-size: 16px;
    }
  }

  &__text1 {
    max-width: 867px;
    text-align: end;
    align-self: end;
    @media @bw400 {
      text-align: start;
    }
  }

  &__text2 {
    grid-area: text;
    margin: 0 80px 0 auto;
    max-width: 870px;
    @media @bw960 {
      text-align: start;
      margin-left: 30px;
      margin-top: -50px;
    }
    @media @bw700 {
      margin-left: auto;
      margin-top: -70px;
    }
  }

  &__block3 {
    display: grid;
    grid-template-columns: 65% 30%;
    gap: 90px 62px;
    justify-content: space-between;
    margin-bottom: 100px;
    grid-template-areas:
      "img text3"
      "img link";
    @media @bw1660 {
      gap: 40px 60px;
    }
    @media @bw1340 {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      margin-bottom: 50px;
    }
    @media @bw1340 {
      margin-bottom: 80px;
    }
    @media @bw650 {
      justify-content: center;
    }
  }

  &__block3-img {
    grid-area: img;
    @media @bw1340 {
      margin-bottom: 80px;
    }
    @media @bw1020 {
      width: 95%;
    }
  }

  &__picture3 {
    position: relative;
    width: 100%;
    height: 100%;
  }

  &__text3 {
    grid-area: text3;
    align-self: flex-end;
    margin-top: 100px;
    @media @bw1660 {
      margin-top: 50px;
    }
    @media @bw1340 {
      margin-top: -50px;
      max-width: 280px;
    }
    @media @bw500 {
      margin-top: -100px;
    }
  }

  &__link {
    grid-area: link;
    display: inline-flex;
    flex-direction: row;
    justify-content: space-between;
    height: 0;
    align-items: center;
    text-decoration: none;
    color: @black;
    transition: color 0.2s;
    &:hover {
      color: @red;
    }
     @media @bw1660 {
      margin-top: 50px;
    }
    @media @bw1340 {
      min-width: 260px;
    }
    @media @bw650 {
      margin-top: 0;
    }
    @media @bw400 {
      font-size: 14px;
    }
  }

  &__link-text {
    font-weight: 600;
    font-size: 16px;
    line-height: 22px;
    text-decoration: none;
  }

  &__link-arrow {
    color: inherit;
    background-color: transparent;
    border-color: transparent;
  }
}

</style>