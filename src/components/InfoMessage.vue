<template>
    <div class="message-bar">
        Proszę wybrać kolor i rozmiar.
    </div>
</template>

<script>
export default {
    name: 'info-message' 
}
</script>

<style lang="scss" scoped>
    .message-bar {
        position: fixed;
        display: flex;
        justify-content: center;
        align-items: center;
        left: 0;
        top: 0;
        right: 0;
        height: 60px;
        background: rgb(243, 78, 49);
        color: #fff;
        letter-spacing: 1px;
        font-weight: 700;
        animation: slideDown .5s ease-in-out;
    }

    @keyframes slideDown {
        0% { top: -100%; }
        100% { top: 0; }
    }

</style>
