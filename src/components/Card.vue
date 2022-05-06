<template>

<div>

  <b-card no-body class="overflow-hidden" style="max-width: 100%">
    <b-row no-gutters>
      <b-col >
        <b-card-img :src="img" alt="Image" class="rounded-0 " style="height: 100%;"></b-card-img>
      </b-col>
      <b-col  cols="8 " class="p-3"> 
        <b-card-title>
        <p contenteditable="true" >{{title}}</p>
       </b-card-title>
        <p contenteditable="true" >{{text}}</p>
        <b-button v-if="Sbutton" href="#" variant="primary">Go somewhere</b-button>
      </b-col>
    </b-row>
  </b-card>

</div>

 
</template>


<script>
export default {
    props: ['img' , 'Sbutton'] ,
    data(){
        return{
            text : 'This is a wider card with supporting text as a natural lead-in to additional content,This is a wider card with supporting text as a natural lead-in to additional content',
            title : 'Heading'
        }
    },
}
</script>

<style scoped>
p{
  outline: none;
}
</style>