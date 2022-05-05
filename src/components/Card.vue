<template>

<div>

  <b-card no-body class="overflow-hidden" style="max-width: 100%">
    <b-row no-gutters>
      <b-col >
        <b-card-img :src="img" alt="Image" class="rounded-0"></b-card-img>
      </b-col>
      <b-col  cols="8"> 
        <b-card-body title="Horizontal Card">
          <b-card-text>
            This is a wider card with supporting text as a natural lead-in to additional content.
          </b-card-text>
            <b-button href="#" variant="primary">Go somewhere</b-button>
        </b-card-body>
      </b-col>
    </b-row>
  </b-card>

</div>

 
</template>


<script>
export default {
    props: ['img'] ,
    data(){
        return{
            
        }
    },
}
</script>

<style scoped>

</style>