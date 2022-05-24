<template>
<div>
  <h4 class="parameter mx-0 ps-3">Media</h4>
    <div class="container h-100 p-0">

        <div class="row g-0 p-0 d-flex align-items-baseline d-flex align-items-baseline">
            <p class="parameter-label col-6 ps-3 ">Layout</p>
                <div class="btns d-flex col-6">
                    <button class="mybtn" @click="changeCardOrder('left')">image left</button>
                    <button class="mybtn" @click="changeCardOrder('right')">image right</button>
                </div>
        </div>
        <div class="row g-0 p-0 d-flex align-items-baseline ">
            <p class="parameter-label col-6 ps-3 ">Colors</p>
                <b-dropdown id="dropdown-1" text="Change Background" class="my-2 col-6" >
                    <b-dropdown-item @click="changeCardBackground('white')">White</b-dropdown-item>
                    <b-dropdown-item @click="changeCardBackground('light gray')">Light Gray</b-dropdown-item>
                    <b-dropdown-item @click="changeCardBackground('dark gray')">Dark Gray</b-dropdown-item>
                </b-dropdown>
        </div>
        <div class="row g-0 p-0 d-flex align-items-baseline ">
            
            <p class="parameter-label col-6 ps-3 ">Button</p>
            <div class="icns col-6">
                <b-icon ref="icon" @click="handleCardButton('del')" icon="archive-fill" aria-hidden="true" variant="light" style="cursor : pointer"></b-icon>
                <b-icon ref="icon"  @click="handleCardButton('add')" icon="plus-lg" aria-hidden="true"  variant="light" style="cursor : pointer"></b-icon>
                <div></div>
            </div>
        </div>
        <div class="row g-0 p-0 d-flex align-items-baseline ">
            <p class="parameter-label col-6 ps-3 ">Image</p>
            <div class="d-flex col-6">               
               <div class="image-upload ">
                    <label for="cardFile">
                        <b-icon icon="camera"  variant="light" aria-hidden="true" style="cursor: pointer;"></b-icon>
                    </label>
                    <input class="form-control" type="file" accept="image/*" id="cardFile" @input="uploadImg">
                </div>
            </div>
        </div>
        <div class="row g-0 p-0 d-flex align-items-baseline ">
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
                    <b-dropdown-item   @click="handleBorderStyle('groove')">groove</b-dropdown-item>
                    <b-dropdown-item   @click="handleBorderStyle('ridge')">ridge</b-dropdown-item>
                    <b-dropdown-item   @click="handleBorderStyle('inset')">inset</b-dropdown-item>


                </b-dropdown>
                </div>
            </div>
        </div>

        <div class="row g-0 p-0 d-flex align-items-baseline ">
            <p class="parameter-label col-6 ps-3 ">Round Corners</p>
                <div class="borderControl col-6">
                    <input type="number"  min="0" max="100" v-model="radius" @change="handleBorder($event,'radius')"/>
                    <span>px</span>
                </div>
        </div>

                    <div class="row g-0 p-0 align-items-baseline shadow-div">
                <p class="parameter-label col-6 ps-3" >Shadow</p>
                <div class="d-flex col-6">
                    <b-button class="btn" :class="{focused:!active}" @click="handleShadowBtn">None</b-button>
                     <b-button class="btn" :class="{focused:active}"  @click="handleShadowBtn"><svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Capa_1" x="0px" y="0px" width="55.832px" height="55.832px" viewBox="0 0 55.832 55.832" style="enable-background:new 0 0 55.832 55.832;" xml:space="preserve"><g><g><g><path d="M9.166,41.832H6.669C2.991,41.832,0,38.84,0,35.163V11.835c0-3.678,2.992-6.669,6.669-6.669h34.328     c3.678,0,6.669,2.992,6.669,6.669v3.164c0,0.552-0.448,1-1,1H14.835c-2.575,0-4.669,2.095-4.669,4.669v20.164     C10.166,41.385,9.718,41.832,9.166,41.832z M6.669,7.166C4.094,7.166,2,9.261,2,11.835v23.328c0,2.575,2.095,4.669,4.669,4.669     h1.497V20.669c0-3.678,2.992-6.669,6.669-6.669h30.831v-2.164c0-2.575-2.096-4.669-4.669-4.669H6.669V7.166z"></path><path d="M49.163,50.666H14.835c-3.678,0-6.669-2.992-6.669-6.669V20.669c0-3.678,2.992-6.669,6.669-6.669h34.328     c3.678,0,6.669,2.992,6.669,6.669v23.328C55.832,47.674,52.84,50.666,49.163,50.666z M14.835,15.999     c-2.575,0-4.669,2.095-4.669,4.669v23.328c0,2.575,2.095,4.669,4.669,4.669h34.328c2.575,0,4.669-2.095,4.669-4.669V20.669     c0-2.575-2.096-4.669-4.669-4.669L14.835,15.999L14.835,15.999z"/></g></g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g><g></g></svg></b-button>
               </div>       
                </div>

                <div class="shadow-options" v-if="active">

                             <div class="row g-0 p-0 d-flex ">
                                    <p class="parameter-label col-6 ps-3 " style="transform: translate(0, 10px);">&nbsp;&nbsp;⌙ Color</p>
            <input @change="handleShadow($event,'color')" type="color" class="form-control form-control-color border-0 m-0" :value="shadowColor" style="background: #3e3e46" title="Choose your color">
                                </div>

                                <div class="row g-0 p-0 d-flex align-items-baseline ">
                                    <p class="parameter-label col-6 ps-3 ">&nbsp;&nbsp;⌙ Offset (X, Y)</p>
                                        <div class="borderControl col-6 me-1">
                                            <input type="number" v-model="offsetX" min="0" max="100" @change="handleShadow($event,'x')"/>
                                            <span>px</span>
                                        </div> 
                                        <div class="borderControl col-6">
                                            <input type="number" v-model="offsetY" min="0" max="100" @change="handleShadow($event,'y')"/>
                                            <span>px</span>
                                        </div>
                                </div>
                                
                                <div class="row g-0 p-0 d-flex align-items-baseline ">
                                    <p class="parameter-label col-6 ps-3 ">&nbsp;&nbsp;⌙ Blur</p>
                                        <div class="borderControl col-6">
                                            <input type="number"  v-model="blur" min="0" max="100" @change="handleShadow($event,'blur')"/>
                                            <span>px</span>
                                        </div>
                                </div>
                            
                                <div class="row g-0 p-0 d-flex align-items-baseline ">
                                    <p class="parameter-label col-6 ps-3 ">&nbsp;&nbsp;⌙ Spread</p>
                                        <div class="borderControl col-6">
                                            <input type="number" v-model="spread"  min="0" max="100" @change="handleShadow($event,'spread')"/>
                                            <span>px</span>
                                        </div>
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
            color : "#000000",
            active : false,
            spread : 0,
            blur : 16,
            offsetX : 0,
            offsetY : 8,
            shadowColor : "#000000"
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
        },
        handleShadowBtn(e){
            if(e.target.textContent == 'None'){
            this.active = false
            this.$emit('handleShadowBtn',false)

            }
            else{
                   this.active = true
                   this.$emit('handleShadowBtn',true)

            }
        },
        handleShadow(e,option){

this.$emit('handleShadow',e.target.value,option)
        }
    },
    watch : {
        focusOn : function()
        {
                 this.cardData.map(card =>{
                 if(card.id === this.focusOn){
                this.active = card.shadow.active
                this.spread = card.shadow.spread
                this.blur = card.shadow.blur

                this.shadowColor = card.shadow.color
                this.offsetX = card.shadow.offset.x
                this.offsetY = card.shadow.offset.y

                this.width = card.border.width
                this.radius = card.border.radius
                this.color = card.border.color
                }})
                
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
.shadow-div svg{
    fill:white;
    width : 20px;
    height : 20px;
}
.focused{
    background : #3e3e46;
}
</style>