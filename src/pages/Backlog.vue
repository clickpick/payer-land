<template>
    <div class="backlog">

        <div class="backlog__l">
            <div class="backlog__head">Backlog</div>
        </div>

        <div class="backlog__r">
            <div class="backlog__item">
                <div class="backlog__title">
                    Чат-бот
                </div>
                <div class="backlog__subtitle">
                    Связь с компаниями, планирование досуга,<br>
                    быстрая бронь и подсказки “Куда сходить?”
                </div>
            </div>

            <div class="backlog__item">
                <div class="backlog__title">
                    Бронирование
                </div>
                <div class="backlog__subtitle">
                    Время, столики и всё в этом духе
                </div>
            </div>

            <div class="backlog__item">
                <div class="backlog__title">
                    Интеграция с системами учёта
                </div>
                <div class="backlog__subtitle">
                    Облегчаем жизнь бизнесу с iiko, r-keeper и прочими
                </div>
            </div>

            <div class="backlog__item">
                <div class="backlog__title">
                    Оплата без официанта
                </div>
                <div class="backlog__subtitle">
                    Синхронизация бизнеса с клиентами
                </div>
            </div>
        </div>

    </div>
</template>

<script>
export default {
    name: "v-backlog"
}
</script>

<style lang="postcss">
.backlog {
    min-height: 100vh;
    display: flex;
    align-items: stretch;
}

.backlog__head {
    color: var(--cashier-color);
    font-size: 50px;
    font-weight: 700;
}

.backlog__l, .backlog__r {
    flex-grow: 1;
    flex-shrink: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.backlog__l {
    align-items: flex-end;
    padding-right: 75px;
}

.backlog__r {
    padding-left: 75px;
}

.backlog__item {
    margin: 35px 0;
}

.backlog__title {
    font-size: 25px;
    font-weight: 700;
}

.backlog__subtitle {
    margin-top: 10px;

    font-size: 18px;
    line-height: 1.39em;
    opacity: .5;
}

@media (max-width: 900px) {
    .backlog {
        flex-direction: column;
        padding: 0 30px;
    }

    .backlog__l {
        align-items: flex-start;
        padding-right: 0;
    }

    .backlog__r {
        padding-left: 0;
    }
}

@media (max-width: 900px) {
    .backlog__title {
        font-size: 20px;
    }

    .backlog__subtitle {
        margin-top: 5px;

        font-size: 14px;
    }

    .backlog__item {
        margin: 10px 0;
    }
}
</style>
