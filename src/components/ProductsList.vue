<template>
    <div class="products">
        <h2 class="products__title"
            @click="toggleList">
            <i :class="{ 'fas fa-minus': showProducts, 'fas fa-plus': !showProducts }"></i> {{ title }}
        </h2>

        <div class="products__list" v-if="showProducts">
            <carousel :navigationEnabled="true" :perPage="itemsPerSlide">
                <slide>
                    <img class="products__list-slider-img"     
                         src="https://static.topsecret.pl/public/foto/thumb_104x139/TPO1713SZ_3.jpg" 
                         alt="product image">
                         <div class="products__list-info">
                            <p>T-SHIRT DAMSKI, Z NADRUKIEM</p>
                            <p>TROLL</p>
                            <p class="products__list-price">39.99</p>
                         </div>
                </slide>
                <slide>
                    <img class="products__list-slider-img"
                         src="https://static.topsecret.pl/public/foto/thumb_104x139/TPO1713SZ_1.jpg" 
                         alt="product image">
                         <div class="products__list-info">
                            <p>T-SHIRT DAMSKI, Z NADRUKIEM</p>
                            <p>TROLL</p>
                            <p class="products__list-price">39.99</p>
                         </div>
                </slide>
                <slide>
                    <img class="products__list-slider-img" 
                         src="https://static.topsecret.pl/public/foto/thumb_104x139/TPO1713SZ_3.jpg"
                         alt="product image">
                         <div class="products__list-info">
                            <p>T-SHIRT DAMSKI, Z NADRUKIEM</p>
                            <p>TROLL</p>
                            <p class="products__list-price">39.99</p>
                         </div>                         
                </slide>
                <slide>
                    <img class="products__list-slider-img"
                         src="https://static.topsecret.pl/public/foto/thumb_104x139/TPO1713SZ_1.jpg"
                         alt="product image">
                         <div class="products__list-info">
                            <p>T-SHIRT DAMSKI, Z NADRUKIEM</p>
                            <p>TROLL</p>
                            <p class="products__list-price">39.99</p>
                         </div>
                </slide>
            </carousel>
        </div> 
    </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';

export default {
    name: 'products-list',
    components: {
        Carousel,
        Slide
    },
    props: {
        title: {
            type: String,
            required: true
        },
        itemsPerSlide: {
            type: Number,
            default: 2
        }
    },
    data() {
        return {
            showProducts: true
        }
    },
    methods: {
        toggleList() {
            this.showProducts = !this.showProducts;
        }
    }    
}
</script>

<style lang="scss" scoped>

.products {
    border-top: 1px solid #a19b9b;
    padding: 10px;
    margin-top: 20px;
    text-transform: uppercase;
    text-align: left;
    letter-spacing: 1px;

    &__title {
        font-size: 1rem;
        font-weight: normal;
    }

    &__title:hover {
        text-decoration: underline;
        cursor: pointer;
    }

    &__list {
        padding: 20px 10px;
    }

    &__list-slider-img {
        width: 60%;
    }

    &__list-slider-img:first-child {
        margin-right: 10px;
    }

    &__list-info {
        font-size: .8rem;
    }

    &__list-price {
        text-align: right;
        padding-right: 50px;
    }
}

@media screen and (min-width: 768px) {
    .products__list-info {
        font-size: .9rem;
        padding: 2px;
    }
}
</style>
