<template>
<div class="parameters">

        
        <h4 class="parameter ">Media List</h4>
        <div class="roww d-flex flex-row">
            <p class="parameter-label">Media</p>
          <button @click="addCard" class="mybtn" > Add card</button>
        </div>

    <div class="roww d-flex flex-row">
        <p class="parameter-label">Background</p>
    <b-dropdown id="dropdown-1" text="Change Background" class="my-2" >
        <b-dropdown-item @click="changeBackground('white')">White</b-dropdown-item>
        <b-dropdown-item @click="changeBackground('light gray')">Light Gray</b-dropdown-item>
        <b-dropdown-item @click="changeBackground('dark gray')">Dark Gray</b-dropdown-item>
    </b-dropdown>
    </div>

    <div class="d-flex flex-row roww">
        <p class="parameter-label">Content Width</p>
        <button class="mybtn " @click="changeCardWidth('small')">small</button>
        <button class="mybtn" @click="changeCardWidth('medium')">medium</button>
        <button class="mybtn"  @click="changeCardWidth('big')">big</button>
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