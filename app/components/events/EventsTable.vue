<template>
    <section>
        <h5 class="events-table__title section-title">
            дополнительные услуги
        </h5>
        <p class="events-table__descr">
            Перед запуском проекта, мы подготавливаем подробную смету и
            согласуем ее с клиентом. Убедившись, что все пожеланию учтены и мы
            можем приступать к реализациии проекта, начинается сложная, но
            интересная работа, результатом которой будет проведение вашего
            мероприятия на высшем уровне.
        </p>
        <table class="events-table">
            <thead class="events-table__head">
                <tr class="events-table__head-tr">
                    <th class="events-table__th"></th>
                    <th class="events-table__th">Тариф «Light»</th>
                    <th class="events-table__th">Тариф «Promo»</th>
                    <th class="events-table__th">Тариф «All stars»</th>
                </tr>
            </thead>
            <tbody class="events-table__body">
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Стоимость за час</th>
                    <td class="events-table__td">1 000&nbsp;₽</td>
                    <td class="events-table__td">3 000&nbsp;₽</td>
                    <td class="events-table__td">от 6&nbsp;000&nbsp;₽</td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Ведущий мероприятия</th>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Фотосъемка</th>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Видеосъемка</th>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Организация питания</th>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Декор</th>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Звуковое сопровождение</th>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Дополнительное освещение</th>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
                <tr class="events-table__tr">
                    <th class="events-table__body-th">Клининг</th>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"></td>
                    <td class="events-table__td"><span class="events-table__ok"></span></td>
                </tr>
            </tbody>
            <tfoot class="events-table__foot">
                <tr class="events-table__foot-tr">
                    <th class="events-table__foot-th"></th>
                    <th class="events-table__foot-th">Тариф «Light»</th>
                    <th class="events-table__foot-th">Тариф «Promo»</th>
                    <th class="events-table__foot-th">Тариф «All stars»</th>
                </tr>
            </tfoot>
        </table>
    </section>
</template>

<script setup>
</script>

<style lang="less">
.events-table {
    width: 100%;
    border-collapse: collapse;
    color: @black;
    text-align: center;
    margin-bottom: 50px;

    @media @bw1340 {
        width: 92%;
        margin-left: 40px;
    }

    @media @bw960 {
        width: 94%;
        margin-left: 30px;
        margin-bottom: 40px;
    }

    @media @bw768 {
        width: 92%;
    }

    @media @bw600 {
        width: 100%;
        margin-left: 0;
    }

    &__title {
        font-weight: 400;
        font-size: 22px;
        line-height: 30px;
    }

    &__descr {
        font-weight: 400;
        font-size: 16px;
        max-width: 868px;
        align-self: flex-start;
        margin-bottom: 60px;

        @media @bw1340 {
            margin-left: 30px;
            margin-right: 30px;
        }

        @media @bw500 {
            margin-left: 20px;
            margin-right: 20px;
        }
    }

    &__head,
    &__body,
    &__foot {
        @media @bw600 {
            display: block;
        }
    }

    &__head-tr,
    &__foot-tr {
        @media @bw600 {
            display: flex;
            width: 100%;
        }
    }

    &__th {
        height: 85px;
        font-weight: 600;
        font-size: 18px;
        line-height: 1.39;
        border-right: 1px solid #bfbfbf;

        &:last-child {
            border: none;
        }

        @media @bw960 {
            font-size: 14px;
        }
    }

    &__body-th,
    &__td {
        box-sizing: border-box;
        height: 50px;
    }

    &__body-th {
        text-align: left;
        padding: 13px 15px 12px 0;
        border-top: 1px solid #bfbfbf;
        border-bottom: 1px solid #bfbfbf;
        font-weight: 400;
        font-size: 18px;
        line-height: 1.39;

        @media @bw600 {
            width: 100%;
            text-align: center;
            font-weight: 600;
            font-size: 14px;
        }
    }

    &__tr {
        &:nth-child(2n-1) {
            background-color: fade(@black, 3%);
        }

        @media @bw600 {
            display: flex;
            flex-wrap: wrap;
        }
    }

    &__td {
        padding: 13px 10px 12px;
        font-weight: 600;
        font-size: 16px;
        line-height: 1.375;
        border: 1px solid #bfbfbf;

        &:last-child {
            border-right: none;
        }

        @media @bw600 {
            width: 33.3333%;
        }
    }

    &__ok {
        display: block;
        position: relative;
        margin: auto;
        width: 26px;
        height: 26px;
        border-radius: 50%;
        background-color: @black;

        &::after {
            content: "";
            position: absolute;
            left: 9px;
            top: 4px;
            width: 6px;
            height: 12px;
            border-bottom: 2px solid @white;
            border-right: 2px solid @white;
            transform: rotate(45deg);
        }
    }

    &__foot-th {
        height: 60px;
        font-size: 0;
        border-right: 1px solid #bfbfbf;

        &:last-child {
            border: none;
        }

        @media @bw600 {
            font-weight: 300;
            font-size: 14px;
            color: fade(@black, 50%);
        }
    }

    &__th,
    &__foot-th {
        box-sizing: border-box;
        text-transform: uppercase;

        @media @bw600 {
            display: flex;
            justify-content: center;
            align-items: center;
            text-align: center;
            width: 33.3333%;

            &:first-child {
                display: none;
            }
        }
    }
}
</style>