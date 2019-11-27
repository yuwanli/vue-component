<template>
<transition name="fade">
    <div class="popup" :data-type="popupType" @click="popupClick">
        <div class="popup-content" @click.stop>
            <slot>
            </slot>
        </div>
        <slot name="content"></slot>
    </div>
</transition>
</template>
<script>
export default {
    name: 'APP',
    data() {
        return {};
    },
    created() {
    },
    props: {
        defaultClose: {
            type: Boolean,
            default: true,
        },
        popupType: {
            type: String,
            default: 'center',
        },
    },
    methods: {
        popupClick() {
            if (this.defaultClose) {
                this.closePopup();
            }
        },
        closePopup() {
            this.$emit('closePopup');
        },
    },
};
</script>
<style lang="less" scoped>
.popup{
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 10000;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgba(0,0,0,0.6);
    transition: all 0.3s ease;
    &[data-type='top']{
        .popup-content{
            top: 0;
            left: 0;
            z-index: 3000;
            transition: all 0.3s ease;
        }
        &.fade-leave-active{
            background-color: rgba(0,0,0,0.6);
            .popup-content{
                opacity: 1;
                transform: translateY(0);
            }
        }
        &.fade-leave-to{
            background-color: rgba(0,0,0,0);
            .popup-content{
                opacity: 0;
                transform: translateY(-100%);
            }
        }
        &.fade-enter-active{
            background-color: rgba(0,0,0,0);
            .popup-content{
                opacity: 0;
                transform: translateY(-100%);
            }
        }
        &.fade-enter-to{
            background-color: rgba(0,0,0,0.6);
            .popup-content{
                opacity: 1;
                transform: translateY(0);
            }
        }
    }
    &[data-type='bottom']{
        .popup-content{
            bottom: 0;
            left: 0;
            z-index: 3000;
            transition: all 0.3s ease;
        }
        &.fade-leave-active{
            background-color: rgba(0,0,0,0.6);
            .popup-content{
                opacity: 1;
                transform: translateY(0);
            }
        }
        &.fade-leave-to{
            background-color: rgba(0,0,0,0);
            .popup-content{
                opacity: 0;
                transform: translateY(100%);
            }
        }
        &.fade-enter-active{
            background-color: rgba(0,0,0,0);
            .popup-content{
                opacity: 0;
                transform: translateY(100%);
            }
        }
        &.fade-enter-to{
            background-color: rgba(0,0,0,0.8);
            .popup-content{
                opacity: 1;
                transform: translateY(0);
            }
        }
    }
    &[data-type='center']{
        .popup-content{
            position: relative;
            z-index: 3000;
            transition: all 0.3s ease;
            transform-origin: center center;
        }
        &.fade-leave-active{
            background-color: rgba(0,0,0,0.6);
            .popup-content{
                opacity: 1;
            }
        }
        &.fade-leave-to{
            background-color: rgba(0,0,0,0);
            .popup-content{
                opacity: 0;
            }
        }
        &.fade-enter-active{
            background-color: rgba(0,0,0,0);
            .popup-content{
                opacity: 0;
                transform: scale(0);
            }
        }
        &.fade-enter-to{
            background-color: rgba(0,0,0,0.6);
            .popup-content{
                opacity: 1;
                transform: scale(1);
            }
        }
    }
    &-content{
        position: absolute;
    }
}
</style>


