<template>
<div>
  <h4 class="parameter mx-0 ps-3">Media</h4>
    <div class="container h-100 p-0">

        <div class="row g-0 p-0 ">
            <p class="parameter-label col-6 ps-3 ">Layout</p>
                <div class="btns d-flex col-6">
                    <button class="mybtn" @click="changeCardOrder('left')">image left</button>
                    <button class="mybtn" @click="changeCardOrder('right')">image right</button>
                </div>
        </div>
        <div class="row g-0 p-0 ">
            <p class="parameter-label col-6 ps-3 ">Background</p>
                <b-dropdown id="dropdown-1" text="Change Background" class="my-2 col-6" >
                    <b-dropdown-item @click="changeCardBackground('white')">White</b-dropdown-item>
                    <b-dropdown-item @click="changeCardBackground('light gray')">Light Gray</b-dropdown-item>
                    <b-dropdown-item @click="changeCardBackground('dark gray')">Dark Gray</b-dropdown-item>
                </b-dropdown>
        </div>
        <div class="row g-0 p-0 ">
            <p class="parameter-label col-6 ps-3 ">Button</p>
            <div class="icns col-6">
                <b-icon ref="icon" @click="handleCardButton('del')" icon="archive-fill" aria-hidden="true" variant="light" style="cursor : pointer"></b-icon>
                <b-icon ref="icon"  @click="handleCardButton('add')" icon="plus-lg" aria-hidden="true"  variant="light" style="cursor : pointer"></b-icon>
                <div></div>
            </div>
        </div>
        <div class="row g-0 p-0 ">
            <p class="parameter-label col-6 ps-3 ">Image</p>
            <div class="d-flex col-6">               
               <div class="image-upload">
                    <label for="BackGroundFile">
                        <b-icon icon="camera"  variant="light" aria-hidden="true" style="cursor: pointer;"></b-icon>
                    </label>
                    <input class="form-control" type="file" accept="image/*" id="BackGroundFile" @input="uploadImg">
                </div>
            </div>
        </div>
        <div class="row g-0 p-0 ">
            <p class="parameter-label col-6 ps-3 ">Border</p>
            <div class="d-flex col-6 justify-content-between">
                <div class="borderControl mx-0">
                    <input type="number"  min="0" max="100" v-model="width"  @change="handleBorder($event,'width')"/>
                    <span>px</span>
                </div>
                <input type="color" class="form-control form-control-color border-0 m-0" id="exampleColorInput" :value="color" @change="handleBorder($event,'color')" style="background: #3e3e46" title="Choose your color">
                <div>
                <b-dropdown id="dropdown-1" text="style" class="mt-1" >
                    <b-dropdown-item  @click="handleBorderStyle('solid')" >solid</b-dropdown-item>
                    <b-dropdown-item   @click="handleBorderStyle('dotted')" >dotted</b-dropdown-item>
                    <b-dropdown-item   @click="handleBorderStyle('dashed')">dashed</b-dropdown-item>
                </b-dropdown>
                </div>
            </div>
        </div>

        <div class="row g-0 p-0 ">
            <p class="parameter-label col-6 ps-3 ">Round Corners</p>
                <div class="borderControl col-6">
                    <input type="number"  min="0" max="100" v-model="radius" @change="handleBorder($event,'radius')"/>
                    <span>px</span>
                </div>
        </div>
        </div>
</div>
</template>

<script>
export default {
    props : ['cardData','focusOn'],
    data(){
        return{
            width : 0,
            radius : 0,
            color : "black"
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
        handleBorder(e,type){
            this.$emit('handleBorder',e.target.value,type)
        },
        handleBorderStyle(style){
             this.$emit('handleBorderStyle',style)
        }
    },
    watch : {
        focusOn : function()
        {

                this.width = this.cardData[this.focusOn].border.width
                this.radius = this.cardData[this.focusOn].border.radius
                this.color = this.cardData[this.focusOn].border.color
                
        }
    }

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
    justify-content: space-between;
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
    margin-top : 7px;
    border: 1px solid #000000;
    border-radius: 2px;
    background-color: #2b2b33;
    max-width: 40px;
    height : 25px;
    display : flex;
    align-items: center;
    font-size: 12px;
}

span{
    margin-right: 2px;
    color: #60606b;
}
</style>