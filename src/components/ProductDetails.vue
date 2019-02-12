<template>
<div class="product-details">
    <div class="product-details__item">
        <div class="product-details__item-header"
             @click="toggleHeader">
            <i :class="{ 'fas fa-minus': showDetails, 'fas fa-plus': !showDetails }"></i> {{ title }}
        </div>

        <div class="product-details__item-content" v-if="showDetails">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. 
            Repellat doloribus reprehenderit accusamus id, quae incidunt dolor temporibus quia animi exercitationem!
        </div>
    </div>
</div>    
</template>

<script>
export default {
    name: 'product-details',
    props: {
        title: {
            type: String,
            required: true
        },
        isExpanded: {
            type: Boolean,
            default: false
        }
    },
    data() {
        return {
            showDetails: this.isExpanded
        }
    },
    methods: {
        toggleHeader() {
            this.showDetails = !this.showDetails;
        }
    }
}
</script>

<style lang="scss" scoped>

.product-details {
    &__item {
        border: 2px solid #333;
        margin: 10px 0;
    }

    &__item-header {
        display: flex;
        justify-content: space-between;
        text-transform: uppercase;
        font-size: .9rem;
        font-weight: 600; 
        letter-spacing: 1px;
        transition: .1s ease-in-out;
        padding: 10px 5px;
    }

    &__item-header:hover {
        background: #0000001a;
        cursor: pointer;
    }

    &__item-content {
        padding: 10px;
     }

    @keyframes expand {
        from { height: 0; }
        to { height: 150px; }
    }
}

</style>
