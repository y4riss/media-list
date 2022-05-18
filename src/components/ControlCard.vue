<template>
<div>
  <h4 class="parameter">Media</h4>

    <div class="parameters">

        <div class="left">
        <p class="parameter-label">Layout</p>
        <p class="parameter-label">Background</p>
        <p class="parameter-label">Button</p>
        <p class="parameter-label">Image</p>
        <p class="parameter-label">Border</p>
        <p class="parameter-label">Round Corners</p>

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
        <input class="form-control form-control-sm" style="width:100%" type="file" id="formFile" accept="image/*" @input="uploadImg">


        <div class="borderControl">
        <input type="number"  min="0" max="100"  @change="handleBorder"/>
        <span>px</span>
        </div>


  <div class="borderControl">
        <input type="number"  min="0" max="100" @change="handleCorner"/>
        <span>px</span>
        </div>

        </div>
       


       



</div>
</div>
</template>

<script>
export default {
    data(){
        return{
            number : 0,
            width : 0
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
        },
        handleBorder(e){
            if(e.target.value < 0) e.target.value = 0
            else if(e.target.value > 100) e.target.value = 100
            this.$emit('handleBorder',e)
        },
        handleCorner(e){
            if(e.target.value < 0) e.target.value = 0
            else if(e.target.value > 100) e.target.value = 100
            this.$emit('handleCorner',e)
        }

    },

}
</script>

<style scoped>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.icns{
    display: flex;
    justify-content: space-evenly;
    margin : 6px;
}
input[type="number"]{
    box-sizing: content-box;
    padding: 2px;
    border: none;
    outline : none;
    overflow: hidden;
    border-radius: 0;
    background-color: transparent;
    -moz-appearance: textfield;
    color : white;

}
.borderControl{
    margin-top : 1.2em;
    border: 1px solid #000000;
    border-radius: 2px;
    background-color: #2b2b33;
    width: 60px;
    height : 25px;
    display : flex;
    align-items: center;
    font-size: 12px;
}

span{
    margin-right: 4px;
    color: #60606b;
}
</style>