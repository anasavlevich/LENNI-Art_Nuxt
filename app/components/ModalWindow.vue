<template>
    <ClientOnly>
        <teleport to="body">
            <div v-if="isActive" class="modal-window">
                <div class="modal-window__wrapper">
                    <div class="modal-window__sticky-close">
                        <button type="button" title="Закрыть" class="modal-window__x-btn x-btn" @click="close">
                            <SvgIcon class="x-btn__icon" name="close" width="60" height="60" />
                        </button>
                    </div>
                    <div class="modal-window__container">
                        <h2 class="modal-window__title" v-html="title"></h2>

                        <slot></slot>
                    </div>
                </div>
            </div>
        </teleport>
    </ClientOnly>
</template>

<script setup>
const props = defineProps({
    title: {
        type: String,
        default: "",
    },
    name: {
      type: String,
      required: true,
    },
});
const store = useStore();
  const isActive = computed(() => {
    return props.name ? store.modal[props.name] : null;
  });

  const close = () => {
    if (props.name) store.closeModal(props.name);
  };
</script>

<style lang="less">
.modal-window {
    box-sizing: border-box;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    z-index: 110;
    padding: 90px 95px 50px;
    background-color: rgba(28, 27, 27, 0.4);
    backdrop-filter: blur(50px);
    overflow-y: auto;

    &__wrapper {
        box-sizing: border-box;
        position: relative;
        display: flex;
        flex-direction: column;
        width: 100%;
        max-width: 1210px;
        margin: auto;
        background-color: @gray;
        background-image: url(../assets/images/noise.png);
        background-position: 0 0;
        background-size: auto;
        background-repeat: repeat;

        @media @bw960 {
            min-width: 110%;
        }
    }

    &__sticky-close {
        position: sticky;
        top: 0;
        align-self: flex-end;
        width: 0;
        height: 0;
    }

    &__x-btn {
        position: absolute;
        top: -30px;
        right: -30px;
        transition: color 0.2s;

        &:hover {
            color: @red_dark;
        }

        @media @bw600 {
            right: -10px;
            top: -30px;
        }
    }

    &__title {
        box-sizing: border-box;
        display: flex;
        align-items: center;
        margin: -40px 0 70px -85px;
        padding: 10px 85px;
        width: 595px;
        min-height: 80px;
        background-color: @black;
        text-transform: uppercase;
        font-weight: 400;
        font-family: @font2;
        font-size: 22px;
        line-height: 1.36;
        color: @white;
        letter-spacing: 0.02em;
        z-index: 1;

        @media @bw1170 {
            width: 465px;
            padding: 10px 18px;
            margin: -40px 0 70px -25px;
        }

        @media @bw768 {
            max-width: 80%;
            font-size: 18px;
        }

        @media @bw500 {
            max-width: 90%;
            font-size: 14px;
        }

        @media @bw370 {
            min-width: 225px;
        }
    }
}
</style>