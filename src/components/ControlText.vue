<template>

<div>
    <h4 class="parameter ">Inline Text</h4>
  <b-dropdown id="dropdown-1" text="Dropdown Button" class="m-md-2">
    <b-dropdown-item @click="changeText('n')">normal</b-dropdown-item>
    <b-dropdown-item @click="changeText('h1')">header 1 </b-dropdown-item>
    <b-dropdown-item @click="changeText('h2')">header 2</b-dropdown-item>
    <b-dropdown-item @click="changeText('h4')">header 4</b-dropdown-item>
    <b-dropdown-item @click="changeText('h6')">header 6 </b-dropdown-item>
  </b-dropdown>
</div>
</template>

<script>
export default {
    methods: {
        changeText(a) {
            this.$emit('changeText',a) ;
        }
    }
}
</script>

<style>

</style>