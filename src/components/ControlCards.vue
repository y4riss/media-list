<template>
<div >

        <h4 class="parameter ">Media List</h4>

        <div class="parameters">
            <div class="left">
            <p class="parameter-label">Media</p>
            <p class="parameter-label">Background</p>
            <p class="parameter-label">Content Width</p>
            </div>

                <div class="right ">
            <b-button @click="addCard" class="btn" > Add card</b-button>
            <input type="color" class="form-control form-control-color border-0" id="exampleColorInput" value="#FFFFFF" @change="changeBackground" style="background: #3e3e46" title="Choose your color">
            <div class="btns d-flex">
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
        }
    }
}
</script>

<style >
.parameters{
    display: flex;
    align-items: baseline;
}
.left *{
    padding-bottom: 10px;
}
.right{
    display: flex;
    flex-direction: column;
    margin : 6px;
}
.right *{
    margin : 6px ;
}
button:not(:disabled), [type=button]:not(:disabled), [type=reset]:not(:disabled), [type=submit]:not(:disabled){
    font-size : 10px;
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
    font-size : 10px;
    border : none;
    outline : none;
    color : white;
    background : #595964;
    border : 1px solid black;
}
.dropdown-item {
  font-size : 10px;
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
</style>