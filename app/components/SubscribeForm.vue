<template>
  <form class="subscribe-form" novalidate @submit.prevent="onSubmit">
    <h2 class="subscribe-form__title">
      Подпишись и будь в курсе происходящего
    </h2>
    <div class="subscribe-form__wrapper">
      <div class="subscribe-form__field-wrapper">
        <input v-model="email" type="email" placeholder="Email" class="field__input subscribe-form__input" required />
        <span v-if="submitCount && (!email || !emailIsValid)" class="subscribe-form__error field-error">
          {{
            email && !emailIsValid
              ? "Email указан неверно"
              : "Это поле обязательно"
          }}
        </span>
      </div>
      <button type="submit" class="btn subscribe-form__submit">Подписаться</button>
    </div>
    <label class="subscribe-form__check check">
      <span class="subscribe-form__check-caption check__caption--s">
        Согласен на обработку персональных данных
      </span>
      <input v-model="agreement" :true-value="1" :false-value="0" type="checkbox" class="check__input" required />
      <span class="check__mark"></span>
    
    <span v-if="submitCount && !agreement" class="subscribe-form__error subscribe-form__check-error field-error">
      Это поле обязательно
    </span>
    </label>
  </form>
</template>

<script setup>
const email = ref("");
const agreement = ref(0);
const submitCount = ref(0);
const emailIsValid = computed(() => {
  return /^[-\w.]+@([A-z0-9][-A-z0-9]+\.)+[A-z]{2,6}$/.test(email.value);
});
const onSubmit = () => {
  submitCount.value += 1;
  if (!email.value || !emailIsValid.value || !agreement.value) return;
  console.log({ email: email.value, agreement: agreement.value });
  alert("Подписка оформлена");
};

</script>

<style lang="less">
.subscribe-form {
  width: 405px;
  max-width: 100%;

  &__title {
    margin: 0 0 25px;
    font-size: 16px;
    line-height: 22px;

    @media @bw650 {
      margin-left: 25px;
    }

    @media @bw500 {
      margin: 0 40px 15px;
      font-weight: 400;
      font-size: 13px;
      line-height: 18px;
    }
  }

  &__wrapper {
    display: inline-flex;
    flex-direction: row;
    margin-top: 14px;
    margin-left: 17px;

    @media @bw650 {
      display: grid;
      grid-template-areas: "input btn";
      grid-template-columns: 80% 23%;
      width: 105%;
    }

    @media @bw600 {
      grid-template-columns: 80% 23%;
    }

    @media @bw500 {
      grid-template-columns: 72% 30%;
      width: 110%;
    }

    @media @bw400 {
      width: 112%;
    }

    @media @bw370 {
      grid-template-columns: 65% 35%;
      width: 118%;
    }
  }

  &__field-wrapper {
    @media @bw650 {
      max-width: none;
      grid-area: input;
    }
  }

  &__input {
    border-radius: 0;
    max-height: 49px;
    @media @bw400 {
      font-size: 12px;
    }
  }

  &__error {
    @media @bw650 {
      padding-left: 10px;
    }
  }

  &__submit {
    max-height: 49px;
    background-color: @black;
    color: @white;
    font-weight: 400;
    font-size: 14px;
    border: none;

    &:hover {
      background-color: @red_dark;
    }

    @media @bw768 {
      padding: 10px 35px 10px 25px;
    }

    @media @bw650 {
      grid-area: btn;
      padding: 10px auto 10px auto;
    }

    @media @bw600 {
      padding-left: 15px;
    }

    @media @bw400 {
      padding-left: 18px;
      font-size: 12px;
    }
  }

  &__check {
    margin-left: 17px;
    @media @bw650 {
      margin-left: 25px;
    }
  }

  &__check-caption {
    margin-left: 15px;
    font-weight: 300;
    font-size: 14px;

    @media @bw370 {
      &.check__caption--s {
        font-size: 12px;
        font-weight: 400;
        line-height: 15px;
        width: 260px;
        margin-top: -4px;
      }
    }
  }
  &__check-error {
    margin-left: -25px;    
  }
}
</style>