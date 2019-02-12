<template>
    <div class="breadcrumbs">
        <span class="breadcrumbs__back"><i class="fas fa-caret-left"></i> powrót</span>

        <ul class="breadcrumbs__list">
            <li class="breadcrumbs__item">strona główna / </li>
            <li class="breadcrumbs__item">ona / </li>
            <li class="breadcrumbs__item">odzież damska / </li>
            <li class="breadcrumbs__item">t-shirty</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'breadcrumbs'
}
</script>

<style lang="scss" scoped>

.breadcrumbs {
    display: flex;
    text-transform: uppercase;
    align-items: center;
    font-size: 0.8rem;
    cursor: pointer;
    padding: 5px 0;

    &__back {
        display: flex;
        align-items: center;
        color: #000;
    }

    &__list {
        list-style-type: none;
        display: flex;
        color: #333;
        padding: 0;
        margin: 0 0 0 20px;
    }

    &__item {
        padding: 5px;
    }

    &__item:hover {
        text-decoration: underline;
    }

    .fa-caret-left {
        font-size: 1.5rem;
        margin-right: 5px;
    }
}

</style>
