<template>
    <div class="phone">
        <div class="phone__header">
            <div class="phone__title">
                {{title}}
            </div>
            <div class="phone__subtitle">
                {{subtitle}}
            </div>
        </div>
        <div class="phone__mock">
            <img :alt="image" :src="image3x" :srcset="`${image1x}, ${image2x} 2x, ${image3x} 3x`" class="phone__img">
        </div>
    </div>
</template>

<script>
export default {
    name: "v-phone",

    props: {
        title: String,
        subtitle: String,
        image: String
    },

    computed: {
        image3x() {
            return require(`./../assets/${this.image}@3x.jpg`);
        },
        image2x() {
            return require(`./../assets/${this.image}@2x.jpg`);
        },
        image1x() {
            return require(`./../assets/${this.image}.jpg`);
        }
    }
}
</script>

<style>

.phone {
    text-align: center;
    width: 100%;
}

.phone__header {
    height: 80px;
}

.phone__title {
    font-size: 25px;
    font-weight: 700;
}

.phone__subtitle {
    font-size: 18px;
    line-height: 1.39;
    opacity: .5;
    margin-top: 10px;
}

.phone__mock {

    margin-top: 10px;

    width: 100%;
    height: 554px;

    box-shadow: 40px 70px 100px rgba(0, 0, 0, 0.25);
    border-radius: 35px;

    transform: translateY(35px);

    overflow: hidden;
}

.phone__img {
    max-width: 100%;
}

@media (max-width: 1200px) {
    .phone__mock {
        height: 60vh;
    }
}

@media (max-width: 480px) {
    .phone__header {
        height: 120px;
    }

    .phone__mock {
        height: 50vh;
    }
}
</style>
