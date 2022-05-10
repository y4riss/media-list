<template>
<div class="parameters">

        
        <h4 class="parameter ">Media List</h4>
        <div class="roww d-flex flex-row">
            <p class="parameter-label">Media</p>
          <button @click="addCard" class="mybtn" > Add card</button>
        </div>

    <div class="roww d-flex flex-row">
        <p class="parameter-label">Background</p>
        <input type="color" class="form-control form-control-color border-0" id="exampleColorInput" value="#FFFFFF" @change="changeBackground" style="background: #3e3e46" title="Choose your color">
    </div>

    <div class="d-flex flex-row roww">
        <p class="parameter-label">Content Width</p>
        <button class="mybtn " @click="changeCardWidth('small',$event)" @mouseenter="changeCardWidth('small',$event)" @mouseleave="handleMouseLeave">small</button>
        <button class="mybtn" @click="changeCardWidth('medium',$event)"  @mouseenter="changeCardWidth('medium',$event)" @mouseleave="handleMouseLeave">medium</button>
        <button class="mybtn"  @click="changeCardWidth('big',$event)"  @mouseenter="changeCardWidth('big',$event)" @mouseleave="handleMouseLeave">big</button>
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
.parameter {
    font-size: 1em;
    background: #2b2b33;
    padding: .3em;
    color : white;
    margin : 1em 0;
}
.parameter-label {
    color : white;
    font-size: 10px;
    padding-right : 1.3em;
}
.roww{
    justify-content: space-between;
    padding : .3em;
}
.mybtn {
    font-size : 10px;
    border : none;
    outline : none;
    color : white;
    background : rgb(154, 88, 235);
    padding : 0 1em;
    margin : .3em;

}
.mybtn:hover{
    opacity : .9;
}
.mybtn:active{
    opacity : 1;
}
.btn-group > .btn, .btn-group-vertical > .btn{
    font-size : 10px;
    border : none;
    outline : none;
    color : white;
    background : rgb(154, 88, 235);
}
.dropdown-item {
  font-size : 10px;
    border : none;
    outline : none;
    color : white;
    background : rgb(154, 88, 235);
}

</style>