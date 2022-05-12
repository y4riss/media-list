<template>
<div>
  <h4 class="parameter">Media</h4>

    <div class="parameters">

        <div class="left">
        <p class="parameter-label">Layout</p>
        <p class="parameter-label">Background</p>
        <p class="parameter-label">Button</p>
        <p class="parameter-label">Image</p>

        </div>
                
        <div class="right">
    <div class="btns d-flex">
            <button class="mybtn" @click="changeCardOrder('left')">image left</button>
        <button class="mybtn" @click="changeCardOrder('right')">image right</button>
    </div>
    
    
    <b-dropdown id="dropdown-1" text="Change Background" class="my-2" >
        <b-dropdown-item @click="changeCardBackground('white')">White</b-dropdown-item>
        <b-dropdown-item @click="changeCardBackground('light gray')">Light Gray</b-dropdown-item>
        <b-dropdown-item @click="changeCardBackground('dark gray')">Dark Gray</b-dropdown-item>
    </b-dropdown>

        <div class="icns">
        <b-icon ref="icon" @click="handleCardButton('del')" icon="archive-fill" aria-hidden="true"  style="color: #595964;cursor : pointer"></b-icon>
        <b-icon ref="icon"  @click="handleCardButton('add')" icon="plus-lg" aria-hidden="true"  style="color: #595964;cursor : pointer"></b-icon>
</div>
        <input class="form-control form-control-sm" style="width:100%" type="file" id="formFile" accept="image/*" @change="uploadImg">


        </div>
       


       



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
        },
        uploadImg(e){
             this.$emit('uploadImg',e)
        }
    }
}
</script>

<style>
.icns{
    display: flex;
    justify-content: space-evenly;
    margin : 6px;
}
</style>