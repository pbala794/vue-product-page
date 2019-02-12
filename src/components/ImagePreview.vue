<template>
    <div class="thumbs-wrapper">
        <div class="thumbs-col">
            <img v-for="(img, index) of images" :key="index" 
                 :src="img.thumbnailUrl"
                 @click="selectedThumb = index"
                 :class="{'thumbs-col__img--active': selectedThumb === index}"
                 class="thumbs-col__img"
                 alt="product-thumb">
        </div>

        <div class="big-img-col">
            <img :src="images[selectedThumb].baseUrl" alt="big image preview"
                 class="big-img-col__img">
        </div>
    </div>
</template>

<script>
export default {
    name: 'image-preview',
    props: {
        images: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            selectedThumb: 0
        }
    },
}
</script>

<style lang="scss" scoped>

.thumbs-wrapper {
    display: flex;
    justify-content: space-between;
}

.thumbs-col {
    display: flex;
    flex-direction: column;
    width: 20%;

    &__img {
        max-width: 100%;
        height: auto;
        margin: 5px 0;
        border: 1px solid transparent;
        transition: all .1s ease-in-out;
    }

    &__img:hover,
    &__img--active {
        border-color: #333;
        cursor: pointer;
    }
}

.big-img-col {
    &__img {
        max-width: 100%;
        height: auto;
        padding-left: 15px;
    }
}

@media screen and (min-width: 768px) {
    .thumbs-col {
        width: 100px;
    }
}

</style>
