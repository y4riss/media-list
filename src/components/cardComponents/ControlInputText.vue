<template>
  <div>
    <h4 class="parameter mx-0 ps-3">Text</h4>
      <div class="container">
            <div class="ligne">
            <p class="parameter-label ">Heading</p>
            <input v-model="input.title" >
        </div>
          <div class="ligne my-3">
             <p class="parameter-label  ">Content</p>
            <textarea v-model="input.paragraph" rows="20"   ></textarea>
          </div>
          <div class="ligne">
             <p class="parameter-label ">Button</p>
            <input v-model="input.button" >
          </div>
      </div>
    


    
  
  </div>
</template>

<script>


export default {
    props: ['options'],
    data(){
      return{
     
        input : this.options.cardData.find(card => card.id === this.options.focusOn).textInput
      }
    },
  
    watch :{
      options : {
        handler(){
           this.input = this.options.cardData.find(card => card.id === this.options.focusOn).textInput
        },
        deep :true
      }
    }
}

</script>

<style scoped>
  .ligne{
    display: flex;
    align-items: baseline;
    justify-content: space-between;
  }
  input,textarea{
    
    border: 1px solid #000000;
    border-radius: 2px;
    background-color: #2b2b33;
    color : white;
    max-width: 80%;
    height: 25px;
    display: flex;
    align-items: center;
    font-size: 12px;
    outline : none;
  }
  textarea{
    resize : none;
    height:100px;
    padding : .5em;
  }
</style>