<template>
<div>
  <h4 class="parameter">Media</h4>
  <div class="d-flex flex-row roww">
        <p class="parameter-label">Layout</p>
        <button class="mybtn" @click="changeCardOrder('left')">image left</button>
        <button class="mybtn" @click="changeCardOrder('right')">image right</button>
  </div>

      <div class="roww d-flex flex-row">
        <p class="parameter-label">Background</p>
    <b-dropdown id="dropdown-1" text="Change Background" class="my-2" >
        <b-dropdown-item @click="changeCardBackground('white')">White</b-dropdown-item>
        <b-dropdown-item @click="changeCardBackground('light gray')">Light Gray</b-dropdown-item>
        <b-dropdown-item @click="changeCardBackground('dark gray')">Dark Gray</b-dropdown-item>
    </b-dropdown>
    </div>

          <div class="roww d-flex flex-row">
                <p class="parameter-label">Button</p>
        <b-icon ref="icon" @click="handleCardButton('del')" icon="archive-fill" aria-hidden="true"  style="color: #7952b3;cursor : pointer"></b-icon>
        <b-icon ref="icon"  @click="handleCardButton('add')" icon="plus-lg" aria-hidden="true"  style="color: #7952b3;cursor : pointer"></b-icon>
        </div>



</div>
</template>

<script>
export default {
    data(){
        return{
            number : 0
        }
    },
    methods:{
        changeCardOrder(a){
            this.$emit('changeCardOrder',a);
        },
        changeCardBackground(a){
            this.$emit('changeCardBackground',a)
        },
        handleCardButton(action){
            this.$emit('handleCardButton',action)
        }
    }
}
</script>

<style>

</style>