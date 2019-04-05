<template>
    <div class="root" v-bind:class="{ active: result !== null }">
        <div v-if="result !== null">{{ result }}</div>
    </div>
</template>

<script>
  export default {
    name: 'Message',
    props: ['result']
  }
</script>

<style scoped>
.root {
    display: flex;
    width: 100%;
    height: 40px;
    margin-top: 8px;
    justify-content: center;
    align-items: center;
}
.root.active {
    background-color: rgba(255,255,255,.05);
}
</style>