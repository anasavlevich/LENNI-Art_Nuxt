<template>
  <div class="app-contacts">
    <h1 class="section-title">контакты</h1>
    <div class="app-contacts__container">
      <TheMap class="app-contacts__map" />
      <div class="app-contacts__info">        
        <div class="app-contacts__adress">
          <div class="app-contacts__location">
            <picture class="app-contacts__location-pic">
              <source media="(max-width: 370px)" srcset="assets/images/contacts_icons/location_mobile.jpg" />
              <img src="assets/images/contacts_icons/location.jpg" class="app-contacts__location-img" alt="location" />
            </picture>
          </div>
          <div class="app-contacts__text">
            <div class="app-contacts__title app-contacts__title-adress">
              Томск, Красноармейская 146
            </div>
            <div class="app-contacts__details">2 этаж</div>
            <div class="app-contacts__details">оф. 206</div>
          </div>
        </div>
        <div class="app-contacts__rent">
          <div class="app-contacts__home">
            <picture class="app-contacts__home-pic">
              <source media="(max-width: 370px)" srcset="assets/images/contacts_icons/home_mobile.jpg" />
              <img src="assets/images/contacts_icons/home.jpg" class="app-contacts__home-img" alt="home" />
            </picture>
          </div>
          <div class="app-contacts__text">
            <div class="app-contacts__title">Отдел аренды</div>
            <a href="tel:+73822907256" class="app-contacts__details">8 (3822) 90-72-56</a>
            <a href="idat@tusur.ru" class="app-contacts__details">idat@tusur.ru</a>
          </div>
        </div>
        <div class="app-contacts__events">
          <div class="app-contacts__star">
            <picture class="app-contacts__star-pic">
              <source media="(max-width: 370px)" srcset="assets/images/contacts_icons/star_mobile.jpg" />
              <img src="assets/images/contacts_icons/star.jpg" class="app-contacts__star-img" alt="star" />
            </picture>
          </div>
          <div class="app-contacts__text">
            <div class="app-contacts__title">Отдел мероприятий </div>
            <a href="tel:+73822907256" class="app-contacts__details">8 (3822) 90-72-56</a>
            <a href="idat@tusur.ru" class="app-contacts__details">idat@tusur.ru</a>
          </div>
        </div>
      </div>
    </div>
    <span class="app-contacts__decor-text">
      Просто делайте, что нравится,<br />а мы вам поможем
    </span>
  </div>
</template>

<style lang="less">
.app-contacts {
  &__container {
    .container();
    display: grid;
    grid-template-areas:
      "adress map"
      "rent map"
      "events map";

    @media @bw1170 {
      display: flex;
      flex-direction: row;
      align-items: center;
      flex-wrap: wrap;
      gap: 100px 0;
    }
  }

  &__adress {
    grid-area: adress;
  }

  &__rent {
    grid-area: rent;
  }

  &__events {
    grid-area: events;
  }

  &__map {
    grid-area: map;
    width: 752px;
    height: 495px;
    margin-right: 0;
    margin-left: auto;

    @media @bw1170 {
      margin: auto;
      min-width: 90%;
      min-height: 463px;
    }

    @media @bw768 {
      height: 350px;
      min-height: auto;
    }

    @media @bw370 {
      height: 186px;
    }
  }

  &__info {
    @media @bw1170 {
      display: flex;
      flex-direction: row;
      justify-content: space-evenly;
      width: 100%;
      margin-left: -40px;
    }

    @media @bw768 {
      flex-wrap: wrap;
      margin-left: -20px;
    }

    @media @bw500 {
      flex-direction: column;
      align-items: start;
      justify-content: space-between;
      gap: 42px 0;
      width: auto;
      margin-top: -50px;
      margin-left: 0;
    }
  }

  &__adress,
  &__rent,
  &__events {
    display: inline-flex;
    flex-direction: row;
    align-self: center;
    gap: 0 54px;
    align-items: center;
    margin-bottom: 67px;

    @media @bw1170 {
      flex-direction: column;
      text-align: center;
      max-width: 40%;
      margin-top: 0;
      margin-bottom: auto;
    }

    @media @bw500 {
      flex-direction: row;
      align-self: auto;
      text-align: left;
      gap: 10px 40px;
    }
  }

  &__rent {
    margin-right: 20px;
  }

  &__location-pic,
  &__home-pic,
  &__star-pic {
    width: 100%;
    height: 100%;
  }

  &__text {
    display: flex;
    flex-direction: column;
    font-family: @font1;

    @media @bw600 {
      margin-bottom: 20px;
    }

    @media @bw500 {
      margin-left: -30px;
      margin-bottom: 0;
      text-wrap: nowrap;
    }
  }

  &__title {
    font-weight: 600;
    font-size: 20px;
    margin-bottom: 10px;

    @media @bw1340 {
      font-size: 18px;
    }

    @media @bw1170 {
      font-weight: 700;
      font-size: 18px;
    }

    @media @bw768 {
      font-weight: 600;
      font-size: 16px;
      max-width: 110px;
      margin-left: 8px;
    }

    @media @bw500 {
      text-wrap: wrap;
      margin-left: 0;
      margin-bottom: 0;
      font-weight: 600;
      font-size: 14px;
    }
  }

  &__title-adress {
    @media @bw1340 {
      max-width: 200px;
    }

    @media @bw768 {
      max-width: 180px;
    }

    @media @bw1170 {
      max-width: none;
    }
  }

  &__details {
    font-weight: 400;
    font-size: 16px;
    text-decoration: none;
    margin-bottom: 5px;

    @media @bw600 {
      margin-bottom: 0;
    }

    @media @bw500 {
      font-size: 14px;
    }
  }

  &__decor-text {
    text-align: right;
    margin-top: 170px;
    display: table;
    margin-left: auto;
    margin-right: auto;
    font-family: @font3;
    font-weight: 700;
    font-size: 95px;

    @media @bw1660 {
      font-size: 75px;
    }

    @media @bw1340 {
      font-size: 65px;
    }

    @media @bw1170 {
      font-size: 58px;
    }

    @media @bw1020 {
      font-size: 44px;
    }

    @media @bw768 {
      font-size: 50px;
      text-align: center;
    }

    @media @bw600 {
      font-size: 40px;
    }

    @media @bw500 {
      font-size: 34px;
    }

    @media @bw400 {
      font-size: 25px;
      margin-bottom: -20px;
    }
  }
}
</style>