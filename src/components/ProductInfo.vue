<template>
    <div class="product">
        <h1 class="product__name">
            {{ product.name }}
        </h1>

        <span>{{ product.attributes[0].value }} | {{ product.sku }}</span>
        <div>
            <span>ocena:</span> 
            <span class="product__ranking-heart">&#9825;</span> 
            <span class="product__ranking-heart">&#9825;</span> 
            <span class="product__ranking-heart">&#9825;</span> 
            <span class="product__ranking-heart">&#9825;</span> 
            <span class="product__ranking-heart">&#9825;</span>
            <span>opinie (0)</span>
        </div>

        <div class="product__price">
            {{ product.basePriceGross }} {{ product.currency }}
        </div>

        <ColorPicker :colors="product.configurableAttributes.color"></ColorPicker>
    </div>
</template>

<script>
import ColorPicker from './ColorPicker'

export default {
    name: 'product-info',
    components: {
        ColorPicker
    }, 
    props: {
        product: {
            type: Object,
            required: true
        }
    }
}
</script>

<style lang="scss" scoped>

.product {
    margin: 15px 0;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    text-transform: uppercase;
    text-align: left;

    &__name {
        font-size: 1.5rem;
        font-weight: 500;
        letter-spacing: .8px;
        margin-bottom: 10px;
    }

    &__ranking-heart {
        color: #000;
        font-size: 1.2rem;
        padding: 2px;
    }

    &__price {
        width: 100%;
        margin: 10px 0;
        padding: 10px;
        font-size: 1.8rem;
        font-weight: bolder;
    }
}

@media screen and (min-width: 768px) {
    .product {
        &__price {
            border-bottom: 1px solid #333;
            text-align: right;
        }
    }
}

</style>

