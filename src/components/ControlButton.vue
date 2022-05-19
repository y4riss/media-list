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
    </div>

</template>

<script>
export default {
    data(){
        return{
            buttonSize: "small" ,
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
        }
    }
}
</script>

<style>

</style>