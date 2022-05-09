<template>

<div @click="handleDeleteBtn" >
     <slot></slot>
     <div :class="{outsideBorder:showDeleteBtn}">
  <b-card no-body class="overflow-hidden" style="max-width: 100%">
    <b-row no-gutters>
      <b-col  :order="imgLeft">
        <b-card-img :src="img" alt="Image" class="rounded-0 " style="height: 100%;"></b-card-img>
      </b-col>
      <b-col  cols="8 " class="p-4 " :class="{}"> 
        <b-card-title>
        <p contenteditable="true" >{{title}}</p>
       </b-card-title>
        <p contenteditable="true" >{{text}}</p>
        <b-button v-if="Sbutton" href="#" variant="primary">Go somewhere</b-button>
      </b-col>

    </b-row>
  </b-card>
  </div>
</div>

 
</template>


<script>
export default {
    props: ['img' , 'Sbutton' , 'imgLeft','showDeleteBtn','dark','light','gray'] ,
    data(){
        return{
            text : 'This is a wider card with supporting text as a natural lead-in to additional content,This is a wider card with supporting text as a natural lead-in to additional content',
            title : 'Heading',
        }
    },
    methods : {
      handleDeleteBtn(){
        this.$emit('focus')
      }
    },
    
    }
</script>

<style scoped>
p{
  outline: none;
}

.outsideBorder{
  padding : 1em;
box-shadow: 1px 1px 5px #0cb6cc;}
</style>