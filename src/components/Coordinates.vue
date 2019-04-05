<template>
    <section class="root">
        <input id="shadow-input" class="input" type="number" v-bind:value="code"
            v-on:input="code = $event.target.value" :maxlength="7" />
        <Digits v-bind:code="code" @clicked="onCloseClick" />
        <Message v-bind:result="result" />
    </section>
</template>

<script>
    import CryptoJS from 'crypto-js';

    import ciphered from '../config/ciphered';

    import Message from './Message.vue';
    import Digits from './Digits.vue';

    const getCode = function (secret, coord) {
      const bytes = CryptoJS.AES.decrypt(ciphered, secret);
      let result = null;

      try {
        let deciphered = JSON.parse(bytes.toString(CryptoJS.enc.Utf8));
        if (typeof deciphered[coord] != 'undefined') {
          result = deciphered[coord];
        }
      }
      catch (e) {
        /* eslint-disable no-console */
        console.log('*** error');
      }

      return result;
    }

    export default {
        name: 'Coordinates',
        components: {
            Digits,
            Message
        },
        data: function () {
            return {
                code: '',
                result: null
            }
        },
        watch: {
            code: function (newVal) {
                this.result = getCode(newVal.substr(0,5), newVal.substr(5,2));
            }
        },
        methods: {
            onCloseClick: function () {
                this.code = '';
            }
        }
    }
</script>

<style scoped>
.root {
    position: relative;
}
.input {
    position: absolute;
    top: -40px;
    left: 0;
    opacity: 0;
}
</style>