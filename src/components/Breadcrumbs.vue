<template>
    <div class="breadcrumbs">
        <span>powrót</span>

        <ul class="breadcrumbs-list">
            <li class="breadcrumbs-item">strona główna /</li>
            <li class="breadcrumbs-item">ona /</li>
            <li class="breadcrumbs-item">odzież damska /</li>
            <li class="breadcrumbs-item">t-shirty</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'breadcrumbs'
}
</script>

<style scoped>

.breadcrumbs {
    display: flex;
    text-transform: uppercase;
    align-items: center;
    font-size: 0.9rem;
    cursor: pointer;
}

.breadcrumbs-list {
    list-style-type: none;
    display: flex;
    color: #333;
    padding: 0;
    margin: 0 0 0 20px;
}

.breadcrumbs-item {
    padding: 5px;
}

.breadcrumbs-item:hover {
    border-bottom: 1px solid #333;
}

</style>
