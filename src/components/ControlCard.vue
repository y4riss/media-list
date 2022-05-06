<template>
<div>
  <h4 class="text-light">Media</h4>
  <div class="d-flex flex-row">
        <button class="btn btn-light mx-1" @click="changeCardOrder('left')">image left</button>
        <button class="btn btn-light  mx-1" @click="changeCardOrder('right')">image right</button>
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