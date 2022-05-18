<template>
<div >

        <h4 class="parameter mx-0 ps-3">Media List</h4>

        <div class="container-fluid h-100 p-0">
            
            <div class="row g-0 p-0 ">
                <p class="parameter-label col ps-3 ">Media</p>
                <b-button @click="addCard" class="btn col p-0" > Add card</b-button>
            </div>

            <div class="row g-0 p-0">
                <p class="parameter-label col ps-3">Background</p>
                <div class="d-flex  col">
                    <input type="color" class="form-control form-control-color border-0" id="exampleColorInput" value="#FFFFFF" @change="changeBackground" style="background: #3e3e46" title="Choose your color">
                    <div class="image-upload">
                        <label for="BackGroundFile">
                            <b-icon icon="camera"  variant="light" aria-hidden="true" style="cursor: pointer;"></b-icon>
                        </label>
                        <input class="form-control" type="file" accept="image/*" id="BackGroundFile" @change="uploadImg">
                    </div>
                </div>
            </div>
            
            <div class="row g-0 p-0">
                <p class="parameter-label col ps-3">Content Width</p>
                <div class="btns d-flex col">
                    <b-button class="btn  " @click="changeCardWidth('small',$event)" @mouseenter="changeCardWidth('small',$event)" @mouseleave="handleMouseLeave">small</b-button>
                    <b-button class="btn " @click="changeCardWidth('medium',$event)"  @mouseenter="changeCardWidth('medium',$event)" @mouseleave="handleMouseLeave">medium</b-button>
                    <b-button class="btn "  @click="changeCardWidth('big',$event)"  @mouseenter="changeCardWidth('big',$event)" @mouseleave="handleMouseLeave">big</b-button>
                </div>
            </div>

            


</div>
</div>
  
</template>

<script>
export default {

    methods: {
        addCard () {
            this.$emit('addCard') ;
        },
        changeBackground(e){
            console.log(e.target.value);
            this.$emit('changeBackground',e.target.value)
        },
        changeCardWidth (width,e){
            this.$emit('changeCardWidth',width,e)
        },
        handleMouseLeave(e){
            this.$emit('handleMouseLeave',e)
        },
        uploadImg(e){
             this.$emit('uploadImgBackground',e)
        },
    }
}
</script>

<style >
.parameters{
    display: flex;
    align-items: baseline;
}

.right *{
    margin : 6px ;
}
button:not(:disabled), [type=button]:not(:disabled), [type=reset]:not(:disabled), [type=submit]:not(:disabled){
    font-size : 8px;
    border : none;
    outline : none;
    color : white;
    background : #595964;
    border : 1px solid black;
    padding : .3em 1.2em;
    margin : .3em;

}
.btn-check:focus + .btn-secondary, .btn-secondary:focus{
    background: #3b3b43 !important;
    border : 1px solid black !important;
    box-shadow: none !important;
}
.parameter {
    font-size: 1em;
    background: #2b2b33;
    padding: .3em;
    color : white;
    margin : 1em 0;
}
.parameter-label {
    color : rgba(255, 255, 255, 0.897);
    font-size: 12px;
    padding-right : 1.3em;
}


.btn-group > .btn, .btn-group-vertical > .btn{
    font-size : 8px;
    border : none;
    outline : none;
    color : white;
    background : #595964;
    border : 1px solid black;
}
.dropdown-item {
  font-size : 8px;
    border : none;
    outline : none;
    color : white;
    background : #595964;
}
input[type=color].form-control {
    padding : 6px !important;
}
.form-control-color:not(:disabled):not([readonly]){
    box-shadow : none;
}
.btns{
        justify-content : space-evenly;

}
.image-upload>input {
  display: none;
}

</style>