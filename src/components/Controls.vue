<template>
    <div class="controls-bar">
        <span class="controls-bar__item">
            <i class="fas fa-caret-left"></i> 
            <span class="controls-bar__text">poprzedni produkt</span>
        </span>
        <span class="controls-bar__item">
            <span class="controls-bar__text">następny produkt</span> 
            <i class="fas fa-caret-right"></i>
        </span>
    </div>
</template>

<script>
export default {
    name: 'controls'
}
</script>

<style lang="scss" scoped>

.controls-bar {
    display: flex;
    margin: 10px 0;
    justify-content: space-between;
    text-transform: uppercase;

    &__item {
        cursor: pointer;
        transition: all .2s ease-in-out;
        display: flex;
        align-items: center;
        font-size: .9rem;
    }

    &__item:hover {
        color: #000;
    }

    &__text {
        margin: 0 10px;
    }

    .fa-caret-left,
    .fa-caret-right {
        font-size: 1.5rem;
        padding: 2px 10px;
        color: #fff;
        background: #000;
        text-align: center;
    }
}

</style>

