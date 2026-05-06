<template>
    <div class="field">
        <label class="check field__check" :class="{'check--red': red, 'check--disabled': disabled}">
            <input type="checkbox" class="check__input" :value="checkedValue" :checked="checked"
                @change="handleChange" :disabled="disabled"/>
            <span class="check__mark"></span>
            <span class="check__caption check__caption--s" :class="{
                'check__caption--s': smallLabel
            }" v-html="label"></span>
        </label>
        <span v-if="errorMessage && submitCount" class="field__error field-error">
            {{ errorMessage }}
        </span>
    </div>
</template>

<script setup>
import { useField } from "vee-validate";

const props = defineProps({
    name: {
        type: String,
        required: true,
    },
    label: {
        type: String,
        default: "",
    },
    smallLabel: {
        type: Boolean,
        default: false,
    },
    checkedValue: {
        type: [String, Number],
        default: 1,
    },
    rules: {
        type: Object,
        default: () => ({}),
    },
    submitCount: {
        type: Number,
        default: 0,
    },
    red: {
        type: Boolean,
        default: false,
    },
    disabled: {
        type: Boolean,
        default: false,
    },
});
const { checked, errorMessage, handleChange } = useField(
    props.name,
    props.rules,
    {
        type: "checkbox",
        checkedValue: props.checkedValue,
    },
);
</script>

<style lang="less">
.check {
    box-sizing: border-box;
    position: relative;
    display: inline-flex;
    flex-direction: column;
    align-items: flex-start;
    min-height: 24px;
    padding-top: 2px;
    padding-left: 24px;
    margin-top: 15px;
    margin-bottom: 5px;
    color: @black;
    cursor: pointer;

    &__caption {
        margin-left: 15px;
        font-weight: 300;
        font-size: 16px;
        line-height: 22px;
        text-wrap: nowrap;

        @media @bw1020 {
            text-wrap: wrap;
        }

        &--s {
            font-size: 14px;
            line-height: 19px;
        }
    }
}
</style>