<template>
    <form class="event-reserve" @submit="onSubmit">
        <div class="event-reserve__checks">
            <h4 class="event-reserve__section-title">Забронировать столик</h4>
            <FieldCheck v-for="(val, key) in checks" :key="key" :checkedValue="+key" name="table" :label="`${key} стол`"
                :red="val.red || false" :disabled="val.disabled || false" class="event-reserve__check" />
        </div>
        <div class="event-reserve__schemes">
            <div class="event-reserve__scheme-container">
                <h4 class="event-reserve__scheme-title">Сцена</h4>
                <div class="event-reserve__scheme-wrapper">
                    <EventScene :checks="checks" :values="values" @tableClick="OnTableClick"
                        class="event-reserve__scene" />
                </div>
            </div>
        </div>
        <div class="event-reserve__order">
            <h4 class="event-reserve__section-title">Ваши пригласительные билеты</h4>
            <div class="event-reserve__tickets-list">
                <div class="event-reserve__tickets">
                    <div class="event-reserve__qty" data-caption="шт." :data-price="price.red" data-currency="₽">
                        {{ red }}
                    </div>
                    <div class="event-reserve__sum" data-currency="₽">{{ redCost }}</div>
                </div>
                <div class="event-reserve__tickets">
                    <div class="event-reserve__qty" data-caption="шт." :data-price="price.black" data-currency="₽">
                        {{ black }}
                    </div>
                    <div class="event-reserve__sum" data-currency="₽">{{ blackCost }}</div>
                </div>
            </div>
            <div class="event-reserve__total" data-caption="Сумма&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;" data-currency=" ₽">
                {{ redCost + blackCost }}
            </div>
            <button type="submit" class="btn btn--red event-reserve__submit">
                Купить билеты
            </button>
        </div>
        <div class="event-reserve__legend">
            <h4 class="event-reserve__section-title">
                Стоимость пригласительного билета
            </h4>
            <div class="event-reserve__legend1">
                <span class="event-reserve__legend-red"></span>
                <div class="event-reserve__legend-text event-reserve__legend-text--var" data-currency="₽"
                    data-number="1" data-caption="персона">
                    {{ price.red }}</div>
            </div>
            <div class="event-reserve__legend2">
                <span class="event-reserve__legend-black"></span>
                <div class="event-reserve__legend-text event-reserve__legend-text--var" data-currency="₽"
                    data-number="1" data-caption="персона">
                    {{ price.black }}</div>
            </div>
            <h4 class="event-reserve__section-title--s">Примечание</h4>
            <div class="event-reserve__legend-available">
                <SvgIcon class="event-reserve__legend-circles" name="circles" width="36" height="24" />
                <span class="event-reserve__legend-text">доступные места</span>
            </div>
            <div class="event-reserve__legend-booked">
                <span class="event-reserve__legend-gray"></span>
                <span class="event-reserve__legend-text">забронировано</span>
            </div>
        </div>
    </form>
</template>

<script setup>
import { useForm } from 'vee-validate';

const checks = ref({
    1: { red: true },
    2: {},
    3: {},
    4: { red: true },
    5: { disabled: true },
    6: {},
    7: { red: true },
    8: { red: true },
    9: { red: true },
    10: {},
    11: {},
})
const price = ref({ red: 1400, black: 1250 });
const { submitCount, handleSubmit, setFieldValue, values } = useForm({
    initialValues: {
        table: []
    }
})
const black = computed(() => {
    return Array.isArray(values.table) ? values.table.reduce(function (sum, current) {
        return sum + (checks.value[current]?.red ? 0 : 1)
    }, 0) : 0
})
const blackCost = computed(() => black.value * price.value.black)
const red = computed(() => {
    return Array.isArray(values.table) ? values.table.reduce(function (sum, current) {
        return sum + (checks.value[current]?.red ? 1 : 0)
    }, 0) : 0
})
const redCost = computed(() => red.value * price.value.red)
const onSubmit = handleSubmit(SubmitValues => {
    console.log(SubmitValues)
})
const OnTableClick = (table) => {
    if (checks.value[table]?.disabled) return;
    const currentArray = Array.isArray(values.table) ? values.table : [];
    let newArray;
    if (currentArray.includes(table)) {
        newArray = currentArray.filter((check) => check !== table)
    } else {
        newArray = [...currentArray, table]
    }
    setFieldValue("table", newArray);
}
</script>

<style lang="less">
.event-reserve {
    display: grid;
    gap: 65px 11%;
    grid-template-columns: 405px calc(89%-405px);
    grid-template-areas:
        "checks scheme"
        "order legend";
    width: 100%;

    @media @bw1340 {
        gap: 65px 6.5%;
        grid-template-columns: 401px calc(93.5% - 401px);
        margin-bottom: -30px;
    }

    @media @bw1020 {
        gap: 60px;
        grid-template-columns: auto 390px;
        grid-template-areas:
            "scheme scheme"
            "checks legend"
            "checks order";
    }

    @media @bw768 {
        grid-template-columns: 100%;
        grid-template-areas:
            "scheme"
            "legend"
            "checks"
            "order";
        margin-bottom: -50px;
    }

    &__section-title {
        margin-bottom: 20px;
        font-weight: 700;

        @media @bw768 {
            text-align: start;
            font-size: 16px;
            line-height: 1.375;
        }

        &--s {
            font-weight: 600;

            @media @bw1020 {
                font-weight: 700;
            }
        }
    }

    &__checks {
        grid-area: checks;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        margin-top: -55px;

        @media @bw1340 {
            margin-top: auto;
        }

        @media @bw1020 {
            margin-top: -205px;
        }

        @media @bw768 {
            margin-top: 0;
            margin-bottom: -40px;
        }

        .check {
            margin-top: 10px;
            margin-bottom: 0;
        }
    }

    &__schemes {
        grid-area: scheme;
    }

    &__scheme-container {
        display: inline-flex;
        flex-direction: column;
        align-items: center;
        gap: 40px;
    }

    &__scheme-title {
        box-sizing: border-box;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        max-width: 162px;
        min-height: 34px;
        padding: 6px 56px;
        background-color: @black;
        color: @white;
        font-family: @font2;
        font-size: 16px;
        font-weight: 600;
        line-height: 22px;
        text-align: center;
        text-transform: uppercase;

        @media @bw960 {
            font-weight: 700;
            font-size: 11px;
        }
    }

    &__scheme-wrapper {
        position: relative;
        width: 100%;

        &::after {
            content: "";
            display: block;
            width: 100%;
        }
    }

    &__scene {
        //position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }

    &__order {
        grid-area: order;
        display: flex;
        flex-direction: column;

        .event-reserve__section-title {
            align-self: flex-start;
        }
    }

    &__tickets {
        display: flex;
        justify-content: space-between;
        align-items: baseline;
        margin-bottom: 16px;
        font-weight: 400;
        font-size: 16px;

        @media @bw400 {
            font-size: 14px;
        }
    }

    &__qty {
        &::after {
            content: " " attr(data-caption) " | " attr(data-price) " "
                attr(data-currency);
        }
    }

    &__sum {
        &::after {
            content: attr(data-currency);
            margin-left: 4px;
            font-size: 0.95em;
        }
    }

    &__total {
        &::before {
            content: attr(data-caption);
        }

        &::after {
            content: attr(data-currency);
        }

        align-self: center;
        margin-top: 10px;
        font-weight: 600;
        font-size: 20px;
    }

    &__submit {
        width: 100%;
        margin-top: 53px;
        min-width: 280px;
        max-width: 406px;

        @media @bw1660 {
            width: 405px;
        }

        @media @bw960 {
            width: 100%;
            align-self: center;
            max-width: 388px;
        }

        @media @bw370 {
            min-width: 270px;
        }
    }

    &__legend {
        grid-area: legend;
        display: flex;
        flex-direction: column;
        align-items: flex-end;

        @media @bw768 {
            align-items: flex-start;
        }
    }

    &__legend1,
    &__legend2 {
        box-sizing: border-box;
        position: relative;
        display: inline-flex;
        flex-direction: row;
        align-items: center;
        gap: 0 9px;
        margin-bottom: 15px;
        pointer-events: none;
    }

    &__legend-red,
    &__legend-black {
        box-sizing: border-box;
        display: block;
        width: 24px;
        height: 24px;
    }

    &__legend-red {
        background-color: @red;
    }

    &__legend-black {
        background-color: @black;
    }

    &__legend-text {
        font-weight: 400;
        font-size: 14px;
        line-height: 19px;
        text-wrap: nowrap;

        &--var {
            &::after {
                content: " " attr(data-price) " " attr(data-currency) " | "
                    attr(data-number) " " attr(data-caption);
            }
        }
    }

    &__legend-available {
        display: inline-flex;
        flex-direction: row;
        gap: 0 21px;
    }

    &__legend-circles {
        display: block;
        position: relative;
        width: 100%;
        font-size: 0;
        text-decoration: none;
    }

    &__legend-booked {
        box-sizing: border-box;
        position: relative;
        display: inline-flex;
        flex-direction: row;
        align-items: center;
        gap: 0 29px;
        margin-top: 14px;
        pointer-events: none;
    }

    &__legend-gray {
        box-sizing: border-box;
        display: block;
        width: 23px;
        height: 23px;
        border: none;
        border-radius: 50%;
        padding: 3px;
        background-color: @gray_dark;
    }
}

.reserve>div {
    box-sizing: border-box;
    padding: 10px;
    text-align: center;
}
</style>