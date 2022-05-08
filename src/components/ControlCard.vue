<template>
<div>
  <h4 class="parameter">Media</h4>
  <div class="d-flex flex-row roww">
        <p class="parameter-label">Layout</p>
        <button class="mybtn" @click="changeCardOrder('left')">image left</button>
        <button class="mybtn" @click="changeCardOrder('right')">image right</button>
  </div>

</div>
</template>

<script>
export default {
    methods:{
        changeCardOrder(a){
            this.$emit('changeCardOrder',a);
        }
    }
}
</script>

<style>

</style>