<template>
  <div class="container-fluid  p-0">
            
            <div class="row g-0 p-0 d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3 ">Button Size</p>
                <b-dropdown id="dropdown-1" :text="buttonSize" class="my-2 col-6" >
                    <b-dropdown-item @click="changeButtonSize('Small')">Small</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonSize('Medium')">Medium</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonSize('Large')">Large</b-dropdown-item>
                </b-dropdown>
            </div>

            <div class="row g-0 p-0 d-flex align-items-baseline">
                <p class="parameter-label col-6 ps-3 ">Button Color</p>                
                <b-dropdown id="dropdown-1" :text="buttonColor" class="my-2 col-6" >
                    <b-dropdown-item @click="changeButtonColor('Blue','btn-primary')">Blue</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonColor('Red','btn-danger')">Red</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonColor('Green','btn-success')">Green</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonColor('Black','btn-dark')">Black</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonColor('Light','btn-light')">Light</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonColor('Warning','btn-warning')">Warning</b-dropdown-item>
                    <b-dropdown-item @click="changeButtonColor('Gray','btn-secondary')">Gray</b-dropdown-item>
                </b-dropdown>
            </div>

            <div class="row g-0 p-0  ">
                <p class="parameter-label col-6 ps-3 " style="transform: translate(0,8px);">Outline button</p>
                <b-button @click="toggleOutline" class="btn col-6 p-0" >toggle Outline</b-button>
            </div>
    </div>

</template>

<script>
export default {
    data(){
        return{
            buttonSize: "small" ,
            buttonColor: "Blue" ,
        }
    },
    methods:{
        changeButtonSize(s){
            this.buttonSize = s ;
            if (s === 'Small')
                this.$emit('changeButtonSize','btn-sm');
            else if(s === 'Large')
                this.$emit('changeButtonSize','btn-lg');
            else 
                this.$emit('changeButtonSize','');
        },
        changeButtonColor(clr,btsClr){
            this.buttonColor = clr ;
            this.$emit('changeButtonColor',btsClr) ;
        },
        toggleOutline(){
            this.$emit('toggleOutline') ;
        }
        
    }
}
</script>

<style>

</style>