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

  <b-icon ref="icon" class="icon" variant="light" icon="type-bold" aria-hidden="true"  @click="changeWeight('fw-bold')" ></b-icon>
  <button @click="changeWeight('fst-italic')">Italic</button>
  <button @click="changeWeight('text-decoration-underline')">Underline</button>
    <button @click="changeWeight('text-decoration-line-through')">Line-through</button>
</div>
</template>

<script>
export default {
    methods: {
        changeText(a) {
            this.$emit('changeText',a) ;
        },
        changeWeight(a){
          this.$emit('changeWeight',a)
        }
    }
}
</script>

<style scoped>
.icon{
  cursor:pointer;
  background: rgb(154, 88, 235);
}
</style>
