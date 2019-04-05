<template>
    <div class="root">
        <div class="border border-secret"></div>
        <div class="border border-coord"></div>
        <div class="border border-action"></div>
        <div class="digits digits-secret">
            <div v-for="(item, index) in secret" v-bind:key="index">
                &bull;
            </div>
        </div>
        <div class="digits digits-coord">
            <div v-for="(item, index) in coord" v-bind:key="index">
                {{ item }}
            </div>
        </div>
        <label class="label" for="shadow-input"></label>
        <div class="action" v-on:click="onCloseClick">&times;</div>
    </div>
</template>

<script>
export default {
    name: 'Digits',
    props: ['code'],
    data: function () {
        return {
          secret: '',
          coord: ''
        }
    },
    watch: {
        code: function (newVal) {
          this.secret = newVal.split('').slice(0,5);
          this.coord = newVal.split('').slice(5,7);
        }
    },
    methods: {
        onCloseClick () {
            this.$emit('clicked');
        }
    }
}
</script>

<style scoped>
.root {
    width: 280px;
    max-width: 280px;
    height: 35px; /* 280 / 8 */
    background-color: rgba(255,255,255,.05);
    position: relative;
}
.border {
    position: absolute;
    bottom: -4px;
    height: 2px;
}
.border-secret {
    left: 0;
    width: 175px;
    background-color: rgba(255,255,255,.6);
}
.border-coord {
    left: 175px;
    width: 70px;
    background-color: coral;
}
.border-action {
    left: 245px;
    width: 35px;
    background-color: rgba(255,255,255,.2);
}
.digits {
    position: absolute;
    height: 35px;
    display: flex;
    justify-content: space-around;
    align-items: center;
}
.digits-secret {
    left: 0;
    width: 175px;
}
.digits-coord {
    left: 175px;
    width: 70px;
}
label {
    position: absolute;
    display: block;
    height: 35px;
    width: 245px;
}
.action {
    position: absolute;
    height: 35px;
    display: flex;
    left: 245px;
    width: 35px;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    opacity: 0.8;
    cursor: pointer;
    transition: all 200ms ease;
    user-select: none;
}
.action:hover {
    font-size: 24px;
    opacity: 0.8;
}
</style>