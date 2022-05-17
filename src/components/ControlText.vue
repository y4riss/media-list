<template>

<div>
    <h4 class="parameter ">Inline Text</h4>

      <div class="inline-text">
        <b-dropdown id="dropdown-1" text="Choose size" class="m-md-2">
    <b-dropdown-item @click="changeText('n')">normal</b-dropdown-item>
    <b-dropdown-item @click="changeText('display-1')" >header 1 </b-dropdown-item>
    <b-dropdown-item @click="changeText('display-2')">header 2</b-dropdown-item>
    <b-dropdown-item @click="changeText('display-4')">header 4</b-dropdown-item>
    <b-dropdown-item @click="changeText('display-6')">header 6 </b-dropdown-item>
      </b-dropdown>

      <b-icon ref="icon" class="icon me-2" variant="light" icon="type-bold" aria-hidden="true"  @click="changeWeight('fw-bold')" ></b-icon>
  <b-icon ref="icon" class="icon me-2" variant="light" icon="type-italic" aria-hidden="true"  @click="changeWeight('fst-italic')" ></b-icon>
  <b-icon ref="icon" class="icon me-2" variant="light" icon="type-underline" aria-hidden="true" @click="changeWeight('text-decoration-underline')" ></b-icon>
  <b-icon ref="icon" class="icon" variant="light" icon="type-strikethrough" aria-hidden="true" @click="changeWeight('text-decoration-line-through')" ></b-icon>
  <input type="color" class="form-control form-control-color border-0" id="exampleColorInput" value="#2b2b33" @change="changetextColor" style="background: #3e3e46" title="Choose your color">
 
      </div>

      <b-dropdown id="dropdown-1" text="font size" class="m-md-2">
    <b-dropdown-item @click="changeFontSize('initial')">default</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('8px')">&nbsp;8</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('10px')">10 </b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('12px')">12</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('14px')">14</b-dropdown-item>
    <b-dropdown-item @click="changeFontSize('16px')">16 </b-dropdown-item>
      </b-dropdown>

 
</div>
</template>

<script>
export default {
    methods: {
        changeText(a) {
            this.$emit('changeText',a) ;
        },
        changeWeight(a){
          this.$emit('changeWeight',a)
        },
        changetextColor(a){
          this.$emit('changetextColor',a.target.value);
        },
        changeFontSize(a){
          this.$emit('changeFontSize',a);
        }
    }
}
</script>

<style scoped>
.icon{
  cursor:pointer;
  background: #595964;
  transform: scale(1.4);
  border : 1px solid black;
  margin-left : 3px;
}
.inline-text{
  display: flex;
  align-items: center;
}
</style>
