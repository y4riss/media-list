<template>
<div>
    <h4 class="text-light">Media List</h4>
    <button @click="addCard" class="btn btn-light" > Add card</button>
    <div>
    <b-dropdown id="dropdown-1" text="Change background" class="my-2" >
        <b-dropdown-item @click="changeBackground('white')">White</b-dropdown-item>
        <b-dropdown-item @click="changeBackground('light gray')">Light Gray</b-dropdown-item>
        <b-dropdown-item @click="changeBackground('dark gray')">Dark Gray</b-dropdown-item>
    </b-dropdown>
    </div>
    <div class="d-flex flex-row">
        <button class="btn btn-light mx-1" @click="changeCardWidth('small')">small</button>
        <button class="btn btn-light  mx-1" @click="changeCardWidth('medium')">medium</button>
        <button class="btn btn-light  mx-1"  @click="changeCardWidth('big')">big</button>
    </div>

</div>
  
</template>

<script>
export default {
    methods: {
        addCard () {
            this.$emit('addCard') ;
        },
        changeBackground(color){
            this.$emit('changeBackground',color)
        },
        changeCardWidth (width){
            this.$emit('changeCardWidth',width)
        }
    }
}
</script>

<style>

</style>