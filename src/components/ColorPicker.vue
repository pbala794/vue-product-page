<template>
    <div class="color">
        <h2 class="color__title">wybrano: {{ selectedColor !== null ? colors[selectedColor].value : '' }}</h2>
        
        <div class="color__availables">
            <span class="color__item" v-for="(color, index) in colors" :key="color.id"
                  :style="{ background: colorsMap[color.value] }"
                  :class="{'color__item--active': selectedColor === index}"
                  @click="selectColor(index)">
            </span>
        </div>
    </div>
</template>

<script>
import { EventBus } from '../EventBus.js' 

export default {
    name: 'color-picker',
    props: {
        colors: Array,
        required: true
    },
    data() {
        return {
            colorsMap: {
                'Szary': 'grey',
                'Biały': 'white',
                'Czarny': 'black'
            },
            selectedColor: null
        }
    },
    methods: {
        selectColor(index) {
            this.selectedColor = index;
            EventBus.$emit('color-selected', this.selectedColor);
        }
    }
}
</script>

<style lang="scss" scoped>

.color {
    margin: 10px 0;

    &__title {
        font-size: 1rem;
        font-weight: 500;
        margin-bottom: 10px;
    }

    &__item {
        border: 1px solid #333;
        display: inline-block;
        width: 50px;
        height: 30px;
        margin-right: 10px;
        transition: all .1s ease-in-out;
        cursor: pointer;
    }

    &__item--active {
        border: 2px solid #000;
    }
}

</style>

