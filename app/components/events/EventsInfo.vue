<template>
    <div class="events-info">
        <div class="events-info__section">
            <picture class="events-info__pic">
                <source media="(max-width: 370px)" srcset="assets/images/table_info/information_mobile.jpg" />
                <img src="assets/images/table_info/information.jpg" class="events-info__img" alt="information" />
            </picture>
            <h3 class="events-info__title">Цены</h3>
            <span class="events-info__descr">
                Цены, указанные на сайте носят информационный характер. Мы
                придерживаемся индивидуального подхода в работе с клиентом.
            </span>
        </div>
        <div class="events-info__section">
            <picture class="events-info__pic">
                <source media="(max-width: 370px)" srcset="assets/images/table_info/contact_mobile.jpg" />
                <img src="assets/images/table_info/contact.jpg" class="events-info__img" alt="contact" />
            </picture>
            <h3 class="events-info__title">Контакты</h3>
            <div class="events-info__contacts">
                <span>Отдел организации мероприятий</span><br />
                <a href="tel:+73822907256" class="events-info__tel">
                    8 (3822) 90-72-56 </a><br />
                <a href="idat@tusur.ru" class="events-info__url">
                    idat@tusur.ru
                </a>
            </div>
        </div>
        <div class="events-info__section">
            <picture class="events-info__pic">
                <source media="(max-width: 370px)" srcset="assets/images/table_info/handshake_mobile.jpg" />
                <img src="assets/images/table_info/handshake.jpg" class="events-info__img" alt="handshake" />
            </picture>
            <h3 class="events-info__title">Преимущество</h3>
            <span class="events-info__descr">
                Мы имеем все возможности для того, чтобы помочь как малому бизнесу
                и молодым талантам, так и большим корпорациям и холдингам.
            </span>
        </div>
    </div>
</template>

<script setup></script>

<style lang="less">
.events-info {
    box-sizing: border-box;
    display: flex;
    flex-direction: row;
    justify-content: center;
    flex-wrap: wrap;
    gap: 50px 67px;
    margin-top: -100px;
    margin-bottom: 50px;

    &__title {
        margin-bottom: 10px;
        font-size: 20px;
        font-weight: 600;

        @media @bw960 {
            font-size: 18px;
        }

        @media @bw370 {
            font-size: 14px;
            font-weight: 600;
        }
    }

    &__section {
        max-width: 401px;
        min-width: 219px;
        display: inline-flex;
        flex-direction: column;
        align-items: center;

        @media @bw960 {
            max-width: 280px;
        }

        @media @bw600 {
            max-width: 250px;
        }

        @media @bw370 {
            max-width: 224px;
        }
    }

    &__descr,
    &__contacts {
        text-align: center;
        font-weight: 400;
        font-size: 16px;
        line-height: 22px;
        text-wrap: wrap;

        @media @bw960 {
            font-size: 14px;
        }

        @media @bw370 {
            font-size: 13px;
            line-height: 18px;
        }
    }

    &__tel,
    &__url {
        text-decoration: underline transparent;
    }
}
</style>