<template>
    <div class="app" id="app">

        <div class="swiper-button-prev" v-show="currentIndex === 8"></div>
        <div class="swiper-button-next" v-show="currentIndex === 7"></div>

        <div class="app__logo">
            <logo :type="logo"/>
        </div>

        <div class="swiper-container" ref="swiper">
            <!-- Additional required wrapper -->
            <div class="swiper-wrapper" ref="swiperWrapper">
                <!-- Slides -->
                <div class="swiper-slide app__slide">
                    <phone image="catalog"
                           subtitle="Выбери место для досуга не выходя из ВКонтакте. Dark theme ready"
                           title="Каталог проверенных мест"/>
                </div>
                <div class="swiper-slide app__slide">
                    <phone image="bill"
                           subtitle="Во всех подключенных местах можно расплатиться по QR посредством VK Pay"
                           title="Оплати по QR-коду"/>
                </div>
                <div class="swiper-slide app__slide">
                    <phone image="reviews"
                           subtitle="Если твои друзья оценили заведения, ты об этом узнаешь. Так же у мест есть и оценка на базе отзывов всех людей"
                           title="Отзывы людей о месте"/>
                </div>
                <div class="swiper-slide app__slide">
                    <phone image="stories"
                           subtitle="После публикации отзыва, можно сделать историю с этим заведением"
                           title="Истории"/>
                </div>
                <div class="swiper-slide app__slide">
                    <phone image="tips"
                           subtitle="Отблагодарить официантов теперь будет проще простого"
                           title="Чаевые"/>
                </div>

                <div class="swiper-slide app__slide">
                    <phone image="group"
                           subtitle="Чтобы пользоваться кассой, бизнесу достаточно иметь сообщество. Всю информацию приложение возьмёт из группы"
                           title="Интеграция с сообществами"/>
                </div>
                <div class="swiper-slide app__slide">
                    <phone image="start"
                           subtitle="Достаточно подключить платежи в сообществе – и всё готово. Интеграцию c API группы мы cделаем сами"
                           title="Быстрый старт"/>
                </div>
                <div class="swiper-slide app__slide">
                    <phone image="staff"
                           subtitle="Принимать платежи может не только владелец сообщества, но и приглашённые им кассиры"
                           title="Добавление сотрудников"/>
                </div>
                <div class="swiper-slide app__backlog">
                    <transition name="slide-fade-place">
                        <backlog v-if="logo === 'backlog'"/>
                    </transition>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import Swiper from 'swiper';
import Phone from "./components/Phone";
import Logo from "./components/Logo";
import Backlog from "./pages/Backlog";

const SLIDE_BREAK_CASHIER = 4;
const SLIDE_BREAK_BACKLOG = 7;

export default {
    name: 'app',

    components: {
        Backlog,
        Phone,
        Logo
    },

    data() {
        return {
            swiper: null,
            currentIndex: 0
        };
    },

    mounted() {
        this.swiper = new Swiper(this.$refs.swiper, {
            mousewheel: true,
            slidesPerView: 'auto',
            spaceBetween: 160,
            centeredSlides: true,
            navigation: {
                nextEl: '.swiper-button-next',
                prevEl: '.swiper-button-prev',
            },

            on: {
                init: function () {
                    setTimeout(() => {
                        this.slideTo(1, 2000);
                    }, 200);
                    setTimeout(() => {
                        this.slideTo(0);
                        this.slideReset();
                    }, 600);
                },
            },
        });

        this.swiper.on('slideChange', () => {
            this.currentIndex = this.swiper.activeIndex;
        });

        this.$nextTick(() => {
            //
        });
    },

    computed: {
        logo() {
            if (this.currentIndex > SLIDE_BREAK_BACKLOG) {
                return 'backlog';
            }
            if (this.currentIndex > SLIDE_BREAK_CASHIER) {
                return 'cashier';
            }
            return 'place';
        }
    }
}
</script>

<style lang="postcss">
@import "~reset-css/reset.css";
@import "~swiper/css/swiper.css";

:root {
    --places-color: #FF3B30;
    --gray-color: #D9D9D9;
    --cashier-color: #007AFF;
}


body {
    font-family: -apple-system, BlinkMacSystemFont, "San Francisco", "SF Pro",
    "Google Sans", "Noto Sans", Roboto, "Droid Sans", "Open Sans",
    "Helvetica Neue", sans-serif, "Apple Color Emoji", "Android Emoji",
    EmojiSymbols, "Segoe UI Emoji";
    background-color: #fff;
}

.swiper-container {
    position: absolute;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100%;
}

.app__slide {
    width: 375px;
    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.app {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.app__logo {
    display: flex;
    justify-content: center;
}

.app__backlog {
    overflow: auto;
    width: 100%;
}

.slide-fade-up-enter-active {
    transition: all .3s;
}

.slide-fade-up-leave-active {
    transition: all .3s;
}

.slide-fade-up-enter, .slide-fade-up-leave-to
    /* .slide-fade-leave-active до версии 2.1.8 */
{
    transform: translateY(-200px);
    opacity: 0;
}

.slide-fade-place-enter-active {
    transition: all .3s;
}

.slide-fade-place-leave-active {
    transition: all .3s;
}

.slide-fade-place-enter, .slide-fade-place-leave-to
    /* .slide-fade-leave-active до версии 2.1.8 */
{
    transform: translateX(-200px);
    opacity: 0;
}

.slide-fade-cashier-enter-active {
    transition: all .3s;
}

.slide-fade-cashier-leave-active {
    transition: all .3s;
}

.slide-fade-cashier-enter, .slide-fade-cashier-leave-to
    /* .slide-fade-leave-active до версии 2.1.8 */
{
    transform: translateX(200px);
    opacity: 0;
}

@media (max-width: 480px) {
    html, body {
        position: fixed;
        overflow: hidden;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
    }

    .app__slide {
        width: 300px;
    }
}
</style>
