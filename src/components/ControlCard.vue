<template>
  <button @click="addCard" class="btn btn-light"> Add card</button>
</template>

<script>
export default {
    methods: {
        addCard () {
            this.$emit('addCard') ;
        }
    }
}
</script>

<style>

</style>