<template>
    <div class="cart">
        <button class="cart__btn"
                @click="addToCart(product)">
            Do koszyka <i class="fas fa-shopping-basket"></i>
        </button>

        <div class="cart__modal-backdrop"
             v-if="addedToCart"></div>
        
        <div class="cart__confirm-modal" v-if="addedToCart">
            <span class="confirm-modal__close"
                  @click="closeModal"> X
            </span>

            <h2>Produkt pomyślnie dodany do koszyka :)</h2>
            <button class="confirm-modal__btn"
                    @click="closeModal"> Kontynuuj zakupy
            </button>
        </div>
    </div>
</template>

<script>
import { EventBus } from '../EventBus.js'

export default {
    name: 'add-to-cart',
    props: {
        product: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            isColorSelected: false,
            isSizeSelected: false,
            addedToCart: false
        }
    },
    methods: {
        addToCart(product) {
            if (this.isColorSelected && this.isSizeSelected) {
                this.addedToCart = true;
            } else {
                EventBus.$emit('info-message');
            }
        },
        closeModal() {
            this.addedToCart = false;
        }
    },
    mounted() {
        EventBus.$once('color-selected', () => {
            this.isColorSelected = true;
        });
        EventBus.$once('size-selected', () => {
            this.isSizeSelected = true;
        });
    }
}
</script>

<style lang="scss" scoped>

$modalWidth: calc(100% - 50px);

.cart {
    &__btn {
       width: 100%; 
       border: none;
       padding: 10px;
       font-size: 1.2rem;
       text-transform: uppercase;
       background: #222121;
       color: #fff;
       transition: .2s ease-in-out; 
    }

    &__btn:hover {
        background: #000;
        cursor: pointer;
    }

    &__confirm-modal {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
        position: fixed;
        z-index: 10;
        top: 20%;
        left: calc(100vw - $modalWidth);
        width: $modalWidth;
        height: 200px;
        padding-top: 50px;
        background: #fff;
        border: 1px solid rgba(0,0,0,0.2);
        box-shadow: 0 3px 9px rgba(0,0,0,0.5);
        transition: all .2s ease-in-out;
    }

    .confirm-modal__close {
        position: absolute;
        top: 6px;
        right: 6px;
        font-size: 1.8rem;
        font-weight: 900;
        display: inline-block;
        width: 35px;
        height: 35px;
        cursor: pointer;
    }

    .confirm-modal__btn {
        width: 80%;
        height: 40px;
        text-transform: uppercase;
        font-size: 1rem;
        border: none;
        background: #333;
        color: #fff;
        cursor: pointer;
        letter-spacing: 1px;
        transition: all .1s ease-in-out;
    }

    .confirm-modal__btn:hover {
        background: #000;
    }

    &__modal-backdrop {
        position: fixed;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        background: rgba(0, 0, 0, .7);
    }
}

</style>
