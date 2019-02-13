<template>
    <div class="product-track">
        <span class="product-track__item">
            <i class="fas fa-heart"></i> Do schowka
        </span>
        <span class="product-track__item">
            <i class="fas fa-list-ul"></i> Do listy życzeń
        </span>
        <span class="product-track__item">
            <i class="fas fa-map-marker"></i> Dostępność w salonach
        </span>
    </div>
</template>

<script>
export default {
    name: 'track-product'
}
</script>

<style lang="scss" scoped>

.product-track {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-top: 20px;
    text-transform: uppercase;
    font-size: 1rem;

    &__item {
        border: 1px solid #333;
        padding: 8px;
        margin: 0 0 10px;
        display: flex;
        justify-content: center;
        align-content: center;
        width: 48%;
        transition: background .1s ease-in-out;
    }

    &__item:hover {
        cursor: pointer;
        background: rgba(0, 0, 0, .1);
        color: #3d3d3d;
    }

    &__item:last-child {
        flex: 1;
    }

    .fas {
        margin-right: 8px;
    }
}

</style>
