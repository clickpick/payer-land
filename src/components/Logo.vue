<template>
    <transition name="slide-fade-up">
        <div class="logo" v-if="type !== 'backlog'">
            <img alt="hidden" class="hidden" src="./../assets/cashier-logo.svg">


            <div class="logo__wrapper">
                <transition name="slide-fade-place">
                    <img alt="logo" src="./../assets/place-logo.svg" v-if="type === 'place'"/>
                </transition>
                <transition name="slide-fade-cashier">
                    <img alt="logo" src="./../assets/cashier-logo.svg" v-if="type === 'cashier'"/>
                </transition>
            </div>

            <div class="logo__name">
                click.<span class="logo__app logo__app--places" v-if="type === 'place'">места</span><span
                    class="logo__app logo__app--cashier" v-if="type === 'cashier'">касса</span>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    name: "v-logo",

    props: {
        type: String
    }
}
</script>

<style lang="postcss">
.logo {
    display: flex;
    flex-direction: column;
    align-items: center;
    font-weight: 700;
}

.logo__wrapper {
    position: relative;
    width: 150px;
    height: 150px;
}

.logo__wrapper img {
    position: absolute;
}

.logo__name {
    color: var(--gray-color);;
    font-size: 50px;
}

.logo__app--places {
    color: var(--places-color);
}

.logo__app--cashier {
    color: var(--cashier-color);
}

.hidden {
    opacity: 0;
    width: 0;
    height: 0;
    overflow: hidden;
}

@media (max-width: 480px) {
    .logo__name {
        font-size: 30px;
    }

    .logo__wrapper {
        width: 75px;
        height: 75px;
    }

    .logo__wrapper img {
        width: 75px;
        height: 75px;
    }
}
</style>
