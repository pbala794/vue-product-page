<template>
    <div class="sizes">
        <h2 class="sizes__title">Rozmiar</h2>

        <div class="sizes__availables">
            <span class="sizes__item" v-for="(size, index) in sizes" :key="size.id"
                  @click="selectSize(size, index)"
                  :class="{'sizes__item--active': selectedSize === index}">
                {{ size.value }}
            </span>
        </div>
    </div>
</template>

<script>
import EventBus from '../EventBus.js'

export default {
    name: 'size-picker',
    props: {
        sizes: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            selectedSize: null
        }
    },
    methods: {
        selectSize(size, index) {
            this.selectedSize = index;
            EventBus.$emit('size-selected', size);
        }
    }
}
</script>

<style lang="scss" scoped>

    .sizes {
        text-transform: uppercase;
        margin: 10px 0;

        &__title {
            font-size: 1rem;
            font-weight: 500;
            margin: 5px 0;
        }

        &__item {
            display: inline-block;
            outline: 1px solid #333;
            cursor: pointer;
            margin-right: 15px;
            padding: 5px;
            width: 45px;
            height: 35px;
            line-height: 25px;
            text-align: center;
            transition: all .1s ease-in;
        }

        &__item:hover:not(.sizes__item--active) {
            outline: 2px solid #000;
            background: rgba(0, 0, 0, .1);
        }
        
        &__item--active {
            background: #000;
            color: #fff;
        }
    }

</style>
