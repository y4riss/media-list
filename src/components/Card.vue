<template>

<div>

  <b-card no-body class="overflow-hidden" style="max-width: 100%">
    <b-row no-gutters>
      <b-col >
        <b-card-img :src="img" alt="Image" class="rounded-0"></b-card-img>
      </b-col>
      <b-col  cols="8"> 
        <b-card-title>
          <input type="text" v-model="title">
       </b-card-title>
        <b-form-textarea
          style="padding : 0"
          id="textarea-no-resize"
          placeholder="Fixed height textarea"
          rows="3"
          no-resize
          v-model="text"
        ></b-form-textarea>
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
.card{
  padding-right: 5px;
}
textarea.form-control{
  border : none;
}
input[type=text]{
  border : none;
  outline : none;
  margin-top : 1em;
}
</style>